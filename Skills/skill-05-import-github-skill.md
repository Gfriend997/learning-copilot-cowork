---
name: skill-05-import-github-skill
description: |
  Imports a skill from a public GitHub repository into the user's personal Cowork
  skills library. Fetches the source, drafts a SKILL.md adapted to the user's
  domain and role (if they want a reframe), validates it, and stages an
  uploadable copy in the session output so the user can mirror it to OneDrive.
  Use when the user says "import this skill from [GitHub URL]", "I found a skill
  on GitHub, set it up", "turn this repo into a Cowork skill", "adapt this
  skill for my domain", "prepare the folder and md file so I can upload it",
  or "add [repo] as one of my skills". Do NOT use for codifying a workflow from
  scratch with no source repo, modifying an existing personal skill (use the
  `skills` system skill), bulk-importing an entire library without confirmation,
  or installing system-level / built-in skills.
cowork:
  category: automation
  icon: Sparkle
---

# Import GitHub Skill

Turns a skill discovered on GitHub into an installed Cowork skill — local file,
optional OneDrive mirror folder, and an uploadable markdown copy in the session
output.

## When to Use

- The user shares a GitHub URL to a single skill or a skills library
- The user wants a skill from one domain (e.g., engineering) reframed for theirs
  (e.g., product, marketing, ops, sales, customer success)
- The user wants the skill installed locally AND visible in their OneDrive
- The user prefers to upload the .md file themselves rather than have it
  written directly to OneDrive

## When NOT to Use

- No source repo — workflow is entirely from the user's head → suggest a
  playbook-builder approach instead
- Editing or auditing an existing personal skill → use the `skills` system skill
- Modifying built-in Cowork skills (read-only)
- Bulk import of an entire library without per-skill confirmation
- User wants the markdown auto-written into OneDrive — that path has known
  serialization issues; this skill stages for manual upload instead

## Core Principle

**Adapt before installing.** A skill copied verbatim from another domain often
fits awkwardly. Ask the user whether they want a reframe and, if so, translate
the source into their language before saving. Never assume the user's role,
domain, or team.

## Workflow

### Phase 1 — Fetch and Read the Source
1. If the user hasn't given one, ask for the GitHub URL (or repo path + skill
   name)
2. Use `WebFetch` (or `mcp__core__web_fetch`) on the SKILL.md or README
3. Identify the source skill's: core principle, trigger phrases, workflow phases,
   output format, guardrails
4. If the repo contains multiple skills, list them and ask which one(s) to
   import — never batch without confirmation

### Phase 2 — Capture User Context (One Question at a Time)
Before drafting, confirm:

1. **Reframe needed?** "Want me to keep the source skill's domain, or adapt it
   to your work? If adapting, what's your role / domain?"
2. **Naming preference?** "Any naming convention you follow for your skills
   (e.g., numbered prefixes like `skill-01-...`, or just kebab-case names)?
   I'll match it."
3. **OneDrive mirror?** "Do you want me to also create a folder for this skill
   under your OneDrive (e.g., `Documents/Cowork/Skills/`) so you can browse it
   there? If yes, tell me the folder path you use."
4. **Audience scope?** "Just for you, or should this skill be team-shareable?
   (Affects whether examples reference specific people.)"

Skip any question the user has already answered earlier in the conversation.

### Phase 3 — Pick a Name and Slot
1. List existing skills: `ls /mnt/user-config/.claude/skills/`
2. If the user uses numbered prefixes, pick the next free `NN`
3. Choose an **outcome-focused** kebab name (what the skill produces), not a
   mechanism name
   - Bad: `search-and-summarize` (mechanism)
   - Good: `weekly-customer-pulse` (outcome)
4. Confirm the proposed name with the user before drafting

### Phase 4 — Draft the SKILL.md
Use the standard Cowork skill structure:

```
---
name: {name matching folder}
description: |
  {2–3 sentence purpose + trigger phrases + "Do NOT use for..." exclusions}
cowork:
  category: {productivity|communication|analysis|writing|research|automation}
  icon: {Fluent UI PascalCase name, e.g., Lightbulb, Sparkle, Mail}
---

# {Title}

{One-sentence purpose}

## When to Use
- {3–5 specific scenarios}

## When NOT to Use
- {3–5 near-misses that route elsewhere}

## Core Principle
{One sentence — the non-negotiable rule}

## Workflow
### Phase 1 — {Name}
{Steps with specific tools, data sources, decision points}

### Phase 2 — ...

## Templates
{Reusable phrases, query patterns, output formats}

## Guardrails
- {Constraints}

## Common Patterns
| Situation | Move |
|-----------|------|
| ... | ... |
```

Adapt content per the user's Phase 2 answers. If reframing, translate every
section — not just the title.

### Phase 5 — Show, Validate, Save Locally
1. **Show the full draft** and ask: "Here's the draft — anything to adjust
   before I save it?"
2. After approval, save to `/mnt/user-config/.claude/skills/{name}/SKILL.md`
3. Validate (if the validator is available):
   `python scripts/validate_skill.py /mnt/user-config/.claude/skills/{name}/SKILL.md`
4. Fix any FAIL results before proceeding

### Phase 6 — Optional OneDrive Mirror
Only if the user requested it in Phase 2:

1. Resolve the user's target OneDrive parent folder via `GetDriveItem`
2. Create the parent `Skills` folder (or whatever path they specified) if it
   doesn't exist
3. Create the subfolder named after the skill
4. **Do NOT attempt to upload the markdown body via Graph** — the body field
   gets JSON-serialized and pollutes the file. Leave the folder empty.

### Phase 7 — Stage the Upload File
1. Copy the saved SKILL.md to `output/Skills/{name}/{name}.md`
2. `Glob output/Skills/**/*` to confirm the file is in place

### Phase 8 — Hand Off
Tell the user:
- The skill is installed and will auto-load — list the trigger phrases
- If a mirror was created: the OneDrive folder path, and that they can drag the
  staged `.md` into it
- Write-back to OneDrive takes ~35 seconds
- How to invoke the skill in their next message

## Templates

### Source-prompt pattern
> "Paste the GitHub URL (or `owner/repo` + skill name). If the repo has several
> skills, pick one — I'll handle them one at a time."

### Reframe-question pattern
> "Want me to keep this skill in its original domain, or adapt it to yours? If
> adapting, tell me your role and the kind of work it should target."

### Reframe-flag pattern
> "This skill leans heavily on {source-domain-specific concept}. The cleanest
> translation I can offer is {X}, but it's a stretch. Want me to proceed, save
> it verbatim as a reference, or skip it?"

### Handoff pattern
> "Skill installed as `{name}`. Triggers: '{phrase 1}', '{phrase 2}',
> '{phrase 3}'. {If mirror requested:} Folder ready at `{OneDrive path}/{name}/`,
> and the matching `.md` is in your session output — drag it in when you have a
> moment. ~35s for OneDrive to catch up."

## Guardrails

- **One skill per invocation.** No batch imports without explicit confirmation.
- **Ask before assuming context.** Never bake in a role, domain, team, or
  naming convention the user hasn't stated.
- **Show the draft before saving.** Skills calcify behavior — approval first.
- **Never auto-upload markdown to OneDrive.** Stage in `output/` for manual
  upload; do not write polluted placeholder files in OneDrive folders.
- **Never overwrite an existing skill name.** If the chosen name conflicts,
  ask for an alternative.
- **Outcome-focused names.** Push back gently on mechanism names.
- **Source attribution.** Include a short footer in the skill body noting the
  GitHub source URL so the user can find the origin later for updates.
- **Validate before reporting success.** Run the validator if available.

## Common Patterns

| Situation | Move |
|-----------|------|
| Repo has many skills, user says "import all" | Push back — propose top 3 most relevant first; batch the rest after the user confirms quality |
| Source skill doesn't reframe cleanly | Flag it, offer to skip, save verbatim as reference, or proceed anyway |
| User already has a similar skill | Don't duplicate — propose extending the existing one or routing the new one to it |
| OneDrive folder creation fails or user has no OneDrive | Skip the mirror; skills work fine without it |
| GitHub URL points to a README or docs page (no SKILL.md) | Ask the user which section to extract; don't guess |
| User wants the .md written into OneDrive automatically | Explain the body-serialization limitation and offer the staged-output workaround |
| Validator not available in the environment | Note it, do basic structural checks manually (name matches folder, frontmatter present, no empty required sections) |
