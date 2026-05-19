# The Cowork Setup Journey

Five steps to go from "I have access" to "Cowork is my second brain." This is the order I would recommend if you were starting today. Not the messy way I arrived at it; the order I wish I had followed.

Each step builds on the last. Skip ahead and you hit walls. Do them in order and the system compounds.

## Step 1: Personalize Copilot First

Before you touch Cowork, configure Microsoft 365 Copilot's personalized instructions. Cowork inherits this context through Work IQ.

Tell Copilot:

- Your role and what you care about
- How you communicate (formal, terse, etc.)
- The businesses, projects, and people you work with
- What you do NOT want Copilot to do

Why first: Cowork reads Work IQ context for every task. If your Copilot profile is generic, every Cowork output will be too. Garbage in, garbage out.

Coming soon: the exact Copilot personalization prompt template.

## Step 2: Clean Your OneDrive

Cowork pulls signal from your OneDrive and SharePoint when answering anything. If your OneDrive is a chaos folder of "New folder (3)" and "Untitled.docx", Cowork's outputs will reflect that.

The leverage move: use Cowork itself to clean OneDrive. It can rename files, reorganize folders, and propose structures based on the content it sees.

Why this order: clean source data improves every Cowork output downstream. Postpone this and you spend hours fixing low-quality results that were doomed at the input layer.

Coming soon: OneDrive triage and folder-structuring prompt sequences.

## Step 3: Reorganize Your Email

Once OneDrive is clean, point Cowork at your inbox. Have it triage:

- Archive what is done
- Surface what needs a response
- Schedule what is calendarable
- Delete what is noise

Why this order: a clean inbox unblocks your day. Cowork can deliver a meaningful daily briefing only after the inbox represents reality, not three weeks of accumulated noise.

Coming soon: inbox triage prompts and daily briefing setup.

## Step 4: Build Your First Custom Skills

Now you have clean context. Time to teach Cowork your repeatable patterns.

Anything you do more than three times in a month is a candidate for a `SKILL.md` in `/Documents/Cowork/skills/`. Examples:

- Weekly status report
- New client onboarding sequence
- Meeting prep for recurring meeting types
- Monthly board update

Why this order: building skills before context is clean produces brittle skills that compensate for messy inputs. Building skills after context is clean lets each skill draw from real signal.

Coming soon: SKILL.md templates and the "what to skill, what not to skill" decision rule.

## Step 5: Build the Thinking Layer

The final step is the highest-leverage one. Beyond personalized instructions and skills, you build the judgment layer: the `_Compass/` patterns that tell Cowork how YOU think, not just what you do.

This is where Cowork crosses from useful to indispensable. Decision heuristics, tradeoff rules, escalation criteria, working style. The patterns that turn a competent agent into a coworker.

Coming soon: the `_Compass/` builder prompts walkthrough and the thinking-logic framework.

---

Each step will eventually have a corresponding playbook in `_Playbooks/`. Treat this file as the index.
