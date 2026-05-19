# Step 3: Build Your First Custom Skills

**Two paths:** build from scratch, OR import from GitHub.

- **From scratch:** write a `SKILL.md` for a repeatable pattern you already have in your head. Use the checklist below.
- **From GitHub (faster):** install the [`skill-05-import-github-skill`](../Skills/skill-05-import-github-skill.md) importer once, then convert any Claude Code skill from public libraries like [obra/superpowers](https://github.com/obra/superpowers) (18.8k stars) or [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) (12.4k stars). The importer reframes the source skill for your role automatically.

If you do not yet have a clear list of repeatable patterns, start with the GitHub path. The libraries contain hundreds of battle-tested skills; pick what fits and let the importer adapt them.

## Why This Order

By now your Copilot profile is set (Step 1) and your OneDrive is clean (Step 2). Cowork has good context. Now teach it your repeatable patterns.

Building skills before context is clean produces brittle skills that compensate for messy inputs. Building skills after context is clean lets each skill draw from real signal.

## What to Skill, What Not to Skill

A skill is worth building when:

- You do the task more than three times a month
- A SKILL.md would save you 15 minutes or more per run
- The task has a clear, repeatable structure (not heavily improvisational)
- Cowork already has access to the inputs (files in OneDrive, emails in your inbox, calendar data)

Examples of good first skills:

- Weekly status report
- New client onboarding sequence
- Meeting prep for recurring meeting types (1:1s, board meetings, sales reviews)
- Monthly board update
- Customer escalation summary
- Quarterly OKR rollup

Examples of bad first skills:

- One-off creative writing (every output is unique, no template to enforce)
- Strategic decisions (the value is in the human judgment, not the structure)
- Anything sensitive enough that you cannot trust Cowork's first draft

## SKILL.md Structure

Each custom skill lives in its own subfolder at `/Documents/Cowork/skills/<your-skill-name>/`. The folder must contain a file named `SKILL.md` (all caps). YAML frontmatter is required. For the full Cowork folder layout (including `copilot-instructions.md` and `sessions/`), see [The Cowork Folder in OneDrive](../Resources/cowork-folder-structure.md).

Minimum viable skill:

```yaml
---
name: Weekly Report
description: Generates a weekly status report from my recent emails and calendar.
---

Gather my sent emails and calendar events from the past week, then create
a summary document organized by project.
```

That is the entire skill. Cowork interprets the description and instructions natively.

## Path A Checklist: Build from Scratch

- [ ] List every task you do more than three times in a month
- [ ] For each, score against the "What to Skill" criteria above. Keep the ones that score high.
- [ ] Pick ONE candidate to start. Resist the urge to build five at once.
- [ ] Create a subfolder under `/Documents/Cowork/skills/<your-skill-name>/`
- [ ] Create `SKILL.md` inside it with YAML frontmatter (`name:`, `description:`) and instructions in Markdown
- [ ] Open a fresh Cowork chat. Cowork discovers custom skills at conversation start, not mid-conversation.
- [ ] Trigger the skill: *"Run my weekly report skill"* (or similar based on the name)
- [ ] Review the output. Note what is wrong, what is missing, what is verbose.
- [ ] Tune the SKILL.md based on what you noticed. Re-run.
- [ ] Once the skill produces reliable output three runs in a row, move to the next candidate
- [ ] Repeat. Cap at 50 custom skills per user (Microsoft's hard limit).

## Path B Checklist: Import from GitHub

- [ ] Install the importer once: copy [`skill-05-import-github-skill.md`](../Skills/skill-05-import-github-skill.md) into `/Documents/Cowork/skills/skill-05-import-github-skill/SKILL.md` (or any folder name; the file must be named `SKILL.md`)
- [ ] Refresh Cowork. Type `/` in the prompt and verify the importer appears in the skill list.
- [ ] Browse [obra/superpowers](https://github.com/obra/superpowers) or [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills). Pick a skill that maps to something you actually do.
- [ ] In Cowork, paste the GitHub URL to the skill and say: *"Import this skill and adapt it for my role."*
- [ ] Answer the reframe questions: domain, naming preference, OneDrive mirror, team-shareable vs. personal.
- [ ] Review the draft Cowork generates. Adjust before saving.
- [ ] Cowork stages the new `SKILL.md` in `/Documents/Cowork/sessions/`. Move (or copy) it into `/Documents/Cowork/skills/<the-skill-name>/SKILL.md`.
- [ ] Refresh Cowork. Type `/` and verify the new skill loaded.
- [ ] Trigger one of its example phrases to confirm it works.
- [ ] Repeat for the next skill from the library.

## Limits to Know

- 50 custom skills total per user
- 1 MB per SKILL.md
- Up to 20 companion files per skill (10 MB total per skill, useful for reference docs and scripts)
- Skills are discovered at the start of each conversation, not loaded dynamically mid-conversation
- Custom skills are not validated by Microsoft. You are responsible for reviewing every output, especially in the first week of a new skill.

## Common Pitfalls

- **Too vague.** "Write me a status report" with no structure gives Cowork no anchor. Spell out sections, length, audience.
- **Too rigid.** A SKILL.md that enumerates every edge case becomes brittle. Cover the 80% case clearly; let Cowork handle the 20% with its built-in reasoning.
- **No verification step.** Add a final instruction like "Before delivering, check that all sections have content and no placeholder text remains."
- **Building too many at once.** Five half-tuned skills hurt more than two tuned skills. Quality over quantity.
- **Importing verbatim from another domain.** A Claude Code skill written for engineers will feel awkward if you are in marketing. Let the importer reframe it. See the importer's "Adapt before installing" principle.

## What You Have After This Step

- The importer skill installed (Path B) OR at least one hand-built skill working (Path A)
- A pattern for evaluating future skill candidates
- Reliable output from your first skill across multiple runs
- A clear sense of which other tasks deserve to be skills next

When that is true, move to [Step 4: Build the Thinking Layer](04-thinking-layer.md).
