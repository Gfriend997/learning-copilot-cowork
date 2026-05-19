# Guide: copilot-instructions.md

## What It Is

`copilot-instructions.md` is your **personal system prompt for Cowork**: a user-level instruction file loaded into Cowork's context at the start of every session, applied to every conversation. It lives at:

```
OneDrive/Documents/Cowork/copilot-instructions.md
```

Use it for **durable rules** that should apply to every Cowork interaction, not facts about you (those belong in your Compass) and not workflow steps (those belong in skills).

**Note:** This file is observed user behavior, not officially documented by Microsoft. Treat it as a working pattern, not a guaranteed API.

## How It Differs From Other Layers

| Layer | Scope | When loaded | Editable |
|-------|-------|-------------|----------|
| Cowork core | All users | Always | No |
| M365 Copilot Custom Instructions | Platform-wide (just you) | Always | Yes (8,000 char cap) |
| `copilot-instructions.md` | Cowork only (just you) | Every Cowork session | Yes |
| Compass | Just you | Referenced from instructions | Yes |
| Skills | Triggered by intent | On invoke | Yes |

Think of `copilot-instructions.md` as the layer between "what Cowork is" (core) and "what you have taught Cowork over time" (skills + Compass).

## What to Put In It

**Behavioral rules and protocols:**
- "Start every request by reading the daily task list at `<path>`"
- "Always draft external emails; never send without my confirmation"
- "Wrap-up phrases: 'wrap up', 'we are done', 'log today's work'"

**Precedence rules and overrides:**
- Which folder or skill takes priority when guidance conflicts
- When to ask the user vs. proceed with assumptions
- Example: *"When Compass conflicts with generic Cowork instruction, Compass wins."*

**Pointers to other layers:**
- "Daily-task-list workflow lives in the daily-briefing skill; do not duplicate it here."
- "Decision rules live in `OneDrive/Documents/Cowork/_Compass/`."

## What NOT to Put In It

- **Facts about you** (role, manager, projects, communication style). Those belong in your M365 Copilot Custom Instructions or your Compass.
- **Workflow steps** (how to draft a status report). Those belong in `SKILL.md` files.
- **Secrets, credentials, PII.** This file is not encrypted; treat as readable.
- **Long narrative.** Keep rules tight and imperative.

## Limitations

- **Length budget.** Soft cap around 200 lines. Beyond this, content is at risk of being truncated or deprioritized. Keep it tight.
- **No conditional logic.** It is prose, not code. "If X then Y" works as a guideline but Cowork will not execute it like a rule engine.
- **Not a hook.** It cannot force actions on tool events. Automated triggers ("whenever I send an email, do X") need to be skills, not instructions here.
- **No secrets.** File is not encrypted; treat as readable.
- **System wins on conflicts.** If your instruction contradicts a Cowork core rule (safety, identity), the core rule wins.
- **No file globs or wildcards.** Paths must be explicit.
- **Loaded once per session.** Edits do not take effect mid-conversation; open a fresh chat for changes to apply.

## Best Practices

### 1. State rules, not narration

- Yes: "When drafting customer emails, use my customer-voice skill."
- No: "I like emails that sound professional but warm and friendly."

### 2. Use precedence statements

Resolve conflicts up front so Cowork does not have to guess. Example:

> "When Compass conflicts with generic Cowork instruction, Compass wins."

That single line settles dozens of edge cases.

### 3. Point to skills and files; do not duplicate

Cowork has skills and a Compass folder. Reference them; do not repeat their content here. Example:

> "Daily-task-list workflow lives in the daily-briefing skill; do not duplicate."

### 4. Imperative voice plus triggers

- Yes: "Start of every request: check today's task list at `<path>`."
- No: "It would be helpful if you checked the task list."

### 5. Anchor with concrete trigger phrases

Concrete phrases beat fuzzy intent. Example:

> "Wrap-up phrases: 'wrap up', 'log today's work', 'we are done for today'."

Better than "when the conversation ends" because Cowork pattern-matches the literal phrases.

### 6. Order matters; most-important first

The top of the file gets the most attention. Put load-bearing rules (session-start protocols, identity overrides, precedence) above optional preferences.

### 7. Do not duplicate Compass

If a fact or principle belongs in Compass (working style, decision criteria, stakeholders), keep it there. Use `copilot-instructions.md` for behavioral rules that point AT Compass, not for Compass content itself.

### 8. Test changes in a fresh session

Edits do not apply to the current conversation. Open a new Cowork chat to see the new behavior.

### 9. Do not narrate the load

You do not need Cowork to announce "Loading your instructions..." at the start of every session. Just say "Apply rules silently."

## A Minimal Example

```markdown
# Session-Start Protocol

Start of every request:
1. Read today's task list at OneDrive/Documents/Cowork/sessions/today/tasks.md
2. Check whether the request matches an active skill; if yes, use it
3. Otherwise, proceed with the default workflow below

# Precedence

When the Compass folder conflicts with generic Cowork guidance, the Compass wins.
Compass location: OneDrive/Documents/Cowork/_Compass/

# External Communication

Always draft customer emails; never send without my explicit confirmation.
Default tone for external communication: warm, direct, no jargon.

# Wrap-Up

When I say "wrap up", "we are done", or "log today's work":
- Save the conversation outputs to OneDrive/Documents/Cowork/sessions/<date>/
- List unfinished items for tomorrow
- Do not narrate the load; just confirm completion
```

This sample is roughly 20 lines, well under the 200-line budget. Most user files settle in the 30 to 80 line range.

## Related Reading

- [The Cowork Folder in OneDrive](cowork-folder-structure.md) : folder layout, where this file sits
- [Cowork Limitations and Workarounds](cowork-limitations.md) : what Cowork can and cannot do
- [Journey Step 1: Personalize Copilot](../Journey/01-personalize-copilot.md) : M365 Copilot Custom Instructions, the platform-wide layer
- [Journey Step 4: Build the Thinking Layer](../Journey/04-thinking-layer.md) : the Compass folder, which `copilot-instructions.md` should reference
