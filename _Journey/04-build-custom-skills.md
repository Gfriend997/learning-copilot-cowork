# Step 4: Build Your First Custom Skills

**Prompt:** Coming soon. SKILL.md template + "what to skill" decision rule.

## Why This Order

By now your Copilot profile is set (Step 1), your OneDrive is clean (Step 2), and your inbox represents reality (Step 3). Cowork has good context. Now teach it your repeatable patterns.

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

Each custom skill lives in its own subfolder at `/Documents/Cowork/skills/<your-skill-name>/`. The folder must contain a file named `SKILL.md` (all caps). YAML frontmatter is required.

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

## Checklist

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

## What You Have After This Step

- At least one working custom skill in `/Documents/Cowork/skills/`
- A pattern for evaluating future skill candidates
- Reliable output from the first skill across multiple runs
- A clear sense of which other tasks deserve to be skills next

When that is true, move to [Step 5: Build the Thinking Layer](05-thinking-layer.md).
