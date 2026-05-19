# Skills: Capacity and Loading

How many custom skills can you have, what actually limits you, and how Cowork loads them. Affects how you should write descriptions and structure skill folders.

**Note:** This is observed behavior from real-world use, harmonized with Microsoft Learn's documented limits. Cowork uses Claude under the hood, so the progressive-disclosure mechanics described here reflect Claude agent behavior. Treat as a working pattern; specifics may evolve.

## The 50 Cap and What Really Limits You

Microsoft Learn caps custom skills at **50 per user**. That is the documented ceiling.

In practice, the real constraints kick in well before 50:

| Limit | What hits it | Soft threshold |
|---|---|---|
| **Skill index noise** | Each skill's `name` and `description` loads at session start so Cowork knows what is available. Too many overlapping entries make routing hard. | Roughly 30 to 50 skills, depending on how distinct the descriptions are |
| **Description overlap** | Two skills that match similar triggers cause Cowork to pick the wrong one or hesitate. | Hits earlier than the count limit |
| **Disk** | OneDrive sync overhead | Effectively unlimited at any reasonable scale |

The real question is not *count*; it is **whether Cowork can pick the right skill when you ask**. Two skills with overlapping triggers ("draft email" vs. "write email") cause confusion. Audit for trigger overlap, not file count.

## Progressive Disclosure: How Skills Actually Load

This is the key design point: **skills are not fully loaded up front.**

What loads at the start of every conversation:

- The skill's `name` and `description` (the YAML frontmatter)

What does NOT load until the skill is invoked:

- The skill's body (instructions, examples, workflow detail)
- Any companion files in the skill's folder (reference docs, templates, scripts)

The body and companions only enter Cowork's context when the skill is actually invoked, either by you asking explicitly or by Cowork matching the description to your request. This is called **progressive disclosure**.

It is why you can have 30+ skills without bloating the context Cowork carries through every conversation.

## What This Means in Practice

### 1. The `description` field is everything

It is the only thing Cowork sees until invocation. A skill with a vague description is functionally invisible: Cowork will never pick it because it cannot tell what the skill does.

Bad description (vague, no triggers):

```yaml
description: Helps with product work.
```

Good description (specific, lists triggers):

```yaml
description: |
  Use when the user asks to draft a PRD, write product requirements,
  or turn a validated idea into a spec. Triggers on: "write a PRD",
  "draft requirements", "spec this out", "product brief".
```

Spell out the trigger phrases. Cowork pattern-matches against them.

### 2. Skill body can be large without penalty

Because the body only loads on invocation, you can put long reference docs, examples, and multi-step instructions in `SKILL.md` without worrying about context cost during normal conversation. A 500-line skill body is no more expensive at session start than a 5-line one.

The trade-off you ARE paying is the 1 MB per `SKILL.md` cap (Microsoft Learn) and the description quality.

### 3. Splitting a big skill into reference files is free

When a skill grows beyond what you want in `SKILL.md`, factor pieces out:

```
my-skill/
├── SKILL.md          (short, just the core flow)
├── reference.md      (deep detail; loaded only when the flow calls for it)
└── examples/         (templates and samples; loaded only on demand)
```

Cowork reads `reference.md` only when the `SKILL.md` instructions explicitly tell it to. Cowork supports up to 20 companion files per skill, 10 MB total per skill (Microsoft Learn).

### 4. Overlapping descriptions are the real problem

If two skills both describe "use when the user writes an email," Cowork has to pick one and may guess wrong. Symptoms of overlap:

- Cowork invokes the wrong skill for a request
- Cowork hesitates or asks for clarification on requests that should map clearly
- A skill you built rarely fires even though the trigger seems obvious

Fix by sharpening descriptions:

- Make trigger phrases distinct ("draft a customer email" vs. "draft an internal Teams message")
- Add explicit "NOT for" clauses where overlap exists ("Use for X; do NOT use for Y")
- Consolidate if two skills genuinely do the same thing

### 5. Audit your skill set periodically

Every few weeks, scan your skill descriptions:

- Are there two that could both fire on the same request?
- Are any descriptions so vague that you cannot remember what the skill does?
- Are any skills unused? Cowork's `Tasks` view shows which skills get invoked.

The skills folder should be a curated library, not a junk drawer.

## Related Reading

- [Skills folder README](../Skills/README.md) - how to install a skill from this repo
- [Journey Step 3: Build Your First Custom Skills](../Journey/03-build-custom-skills.md) - the build-vs-import decision
- [The Cowork Folder in OneDrive](cowork-folder-structure.md) - where the skills folder sits
- [Cowork Limitations and Workarounds](cowork-limitations.md) - the 50 cap, 1 MB SKILL.md cap, companion file limits
