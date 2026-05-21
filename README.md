# Learning Copilot Cowork

A public learning journal and practical blueprint for configuring Microsoft 365 Copilot Cowork (Agentic Wave 3) for real work.

This is not a feature overview or product review. It is a working notebook from someone configuring this system day-to-day, sharing the patterns that hold up and the ones that do not.

## Video Walkthrough

A short walkthrough of what is in this repo and how the pieces fit together: [The Cowork Blueprint](videos/the-cowork-blueprint.mp4) (community contribution).

## Why This Exists

I started this repo because I could not find much information about how to actually set up and configure Copilot Cowork. The official docs cover features; they do not cover the workflow of going from "I have access" to "this is my daily driver." This is me figuring it out in public.

Every prompt, skill, and reference doc here has been tested multiple times in real Cowork sessions and confirmed to work in my own setup. **Your results may differ.** Cowork's behavior depends on your role, your tenant, your Frontier program enrollment, and what you put in your own Compass. Treat what is here as starting points to adapt, not guaranteed scripts.

If this saves you time:

- **Star the repo** so others can find it
- **Share with a teammate** who is also figuring out Cowork
- **Fork it** and turn it into your own personal Cowork learning journey: keep what works, change what does not, document your version

## What Is Copilot Cowork

Microsoft 365 Copilot Cowork is an agentic AI built into the M365 tenant. It does not just answer questions. It plans, executes, and delivers finished work: drafted emails, formatted documents, scheduled meetings, organized files. Built in collaboration with Anthropic using Claude's agentic model.

The shift it represents:

> "From talking about work to doing work."

What it can do out of the box:

- **Office artifacts**: create and edit Word, Excel, PowerPoint, PDFs
- **Communication**: draft and send emails, post Teams messages, create newsletters
- **Calendar**: schedule meetings, resolve conflicts, deliver daily briefings
- **Research**: enterprise search and deep research synthesis
- **Automation**: scheduled, recurring tasks
- **Files**: browse and organize SharePoint and OneDrive
- **Task views**: monitor progress in lists, kanban boards, or schedule views

What makes it different from regular M365 Copilot:

- **Runs inside your tenant** with your identity and permissions, not as an external suggestion engine
- **Work IQ**: org-level context layer that pulls signal from your mailbox, Teams, files, and calendar
- **Agentic autonomy**: takes multi-step actions, pauses at approval gates for sensitive operations
- **Cross-app orchestration**: a single workflow can span Outlook, Teams, OneDrive, and SharePoint
- **Custom skills**: user-defined workflows as `SKILL.md` files at `OneDrive/Documents/Cowork/skills/`, up to 50 skills per user, no code required

The configuration leverage point is the last one. **Custom skills plus how you structure your Microsoft Graph determine the quality of every output.** This repo is about that leverage.

## Async and Cloud-Native

Two facts that change how you should think about Cowork.

**Cowork only works with files in OneDrive and SharePoint.** Files on your local hard drive are invisible. To work with a local file, upload it to a Cowork chat. The output still lands in OneDrive (specifically `OneDrive/Documents/Cowork/sessions/`), never back on your local drive. If a workflow is not anchored on OneDrive, it is not a Cowork workflow.

**Tasks run in the cloud, not on your machine.** Kick off a multi-step task, close your laptop, drive home. Cowork keeps executing on Microsoft's infrastructure. When you come back online, pick up where it paused, typically at an approval gate. This is what separates Cowork from a desktop assistant: the work continues without you. Schedule a daily briefing for 7 AM and it generates before you wake up. Start a deep-research task before a flight and the report is waiting when you land.

This is the agentic shift. Once you trust it, you stop sitting and waiting for AI to finish.

## Four Layers, One Coworker

The four-step journey assembles four layers into a working Cowork system. One layer is foundational (the substrate Cowork draws from); the other three shape its behavior (how it talks, what it does, how it thinks). Listed below in journey order. Build them in this sequence to compound the leverage.

**Step 1, Voice Layer: Personalization ([page](Journey/01-personalize-copilot.md))**

HOW Cowork talks as you. Tone, length, formality, who you write to and how, what phrases to avoid, when to draft vs. send. Set via the Copilot Personalization Interview. First because it is the fastest setup and pays off immediately.

**Step 2, Foundation Layer: Clean OneDrive ([page](Journey/02-clean-onedrive.md))**

The substrate every other layer draws from. Mess in, mess out. Cowork pulls signal from your OneDrive when answering anything, so the later layers will produce stale output if this one is skipped.

**Step 3, Action Layer: Custom Skills ([page](Journey/03-build-custom-skills.md))**

WHAT Cowork does for you. `SKILL.md` files capturing your repeatable workflows so you stop re-explaining them. Weekly reports, client onboarding, meeting prep, monthly board updates. After the substrate is clean so skills draw from real signal.

**Step 4, Judgment Layer: Compass ([page](Journey/04-thinking-layer.md))**

HOW Cowork thinks like you. The `_Compass/` folder in your OneDrive captures your tradeoff rules, escalation criteria, and decision principles. Last because it captures revealed preferences you only notice after using Cowork on real work.

### When the Layers Combine

When all three layers are in place on top of a clean substrate, Cowork stops feeling like a chatbot that answers questions. It starts feeling like a coworker who:

- Writes in your voice without you reviewing every word
- Handles your recurring tasks without re-explanation
- Decides the way you would when you are not available to ask
- Asks you the questions YOU would ask if you were reviewing your own thinking
- Tailors its suggestions to the tradeoffs you actually care about

That last pair is where the system shifts from "tool" to "thinking partner." The Voice layer makes outputs sound like you. The Compass layer makes Cowork's questions and suggestions match how you interrogate a decision. When you face an ambiguous call, Cowork surfaces the same dimensions you would weigh, not generic ones. The interaction becomes a back-and-forth that sharpens your thinking, not a Q&A loop that just produces content.

Skip a layer and the system feels off:

- **No Voice** - every output sounds generic, like it could have come from anyone
- **No Action** - you re-explain the same patterns every time you run them
- **No Judgment** - Cowork's decisions feel competent but not yours
- **No Foundation** - even good layers produce stale answers from a messy source

The journey order is deliberate. Voice first because it is the fastest setup and pays off immediately. Substrate next because the later layers will draw from it. Action before Judgment because building skills before context is clean produces brittle skills. Judgment last because it captures revealed preferences you only notice after using Cowork on real work.

## What You Will Find Here

Most-useful-first; the two "Coming Soon" folders sit at the end.

**[`Journey/`](Journey/)** - The recommended four-step setup path, one page per step: personalize Copilot, clean OneDrive, build custom skills, build the thinking layer. Start here.

**[`FAQ.md`](FAQ.md)** - Common questions answered as they come up (scheduling recurring prompts, etc.). Quick reads, not deep dives.

**[`Resources/`](Resources/)** - External references and deep-dive docs: Microsoft Learn, announcement blogs, community write-ups, the Cowork folder layout, copilot-instructions guide, skills capacity and loading, full limitations table. Read these to ground yourself in how Cowork actually behaves.

**[`Prompts/`](Prompts/)** - Reusable prompt files referenced by the journey: the Copilot Personalization Interview, the OneDrive Cleanup Prompt, and the Compass Builder. Paste these into a fresh Cowork chat to run.

**[`Skills/`](Skills/)** - Installable Cowork skills. Drop a `SKILL.md` into your `OneDrive/Documents/Cowork/skills/<name>/` folder, refresh Cowork, and the skill activates on its trigger phrases. Includes a GitHub-skill importer that converts Claude Code skills into Cowork skills.

**[`Templates/`](Templates/)** - Reusable document and workflow templates. Placeholder; first templates land as patterns stabilize.

**[`Playbooks/`](Playbooks/)** - Structured guides for specific project types (Support Scaling, Venture Launch, Community Management). Placeholder; first playbook lands once the journey is battle-tested by a few readers.

## Key Concepts

**The Operational Brain** - SharePoint and OneDrive are not just file storage. They are Cowork's knowledge layer. How you structure them determines the quality of everything Cowork produces.

**Context Fencing** - If you run multiple businesses or projects, you need architectural patterns that prevent data bleed. Cowork should never pull context from Business A when working on Business B.

**Work IQ** - Cowork's reasoning capability improves with better-structured source data, not more data. Quality over quantity, every time.

**Your Compass** - Skills tell Cowork what to do. Projects tell Cowork what is happening. Your Compass (a folder of decision principles, working style, and escalation rules in your OneDrive) tells Cowork who you are as a leader. You build your own Compass in Journey Step 4 using the Compass Builder prompt. This repo does not ship a sample Compass; it is personal to each user.

## Cowork Conventions and Nuances

What I have learned about how Cowork actually behaves, beyond the official docs. Worth knowing before you start.

### Folder Conventions

- **The `_` prefix.** Cowork's file browser sorts folders starting with `_` to the top. We use this in OneDrive (for example, `_Compass/`) so user-created system folders stay near the Cowork-managed `skills/` and `sessions/` folders. This repo does NOT use the prefix because GitHub sorts alphabetically and `_` only adds noise.
- **`skills/` and `sessions/` are lowercase.** Per Microsoft Learn. Even though OneDrive is case-insensitive on display, use lowercase to match the canonical paths.
- **Folder name vs. SKILL.md `name:` field.** Cowork uses the `name:` in YAML frontmatter, not the folder name. `weekly-report/SKILL.md` and `wkr/SKILL.md` are equivalent if both have `name: Weekly Report`. The folder name is only for your own organization.

### Skills and Sessions

- **50 custom skills max.** Microsoft's hard limit. Choose them deliberately. See [`Resources/cowork-limitations.md`](Resources/cowork-limitations.md) for all limits.
- **Discovery happens at session start.** Cowork scans `OneDrive/Documents/Cowork/skills/` when you open a new chat. Adding a SKILL.md mid-conversation does NOT load it. Open a fresh chat to pick up new skills.
- **`SKILL.md` is case-sensitive.** All caps. `skill.md` will not be discovered.
- **The sessions-to-skills hop.** When Cowork generates a SKILL.md (for example, via the GitHub Skill Importer), the file lands in `sessions/`, not `skills/`. Move it manually to `OneDrive/Documents/Cowork/skills/<your-name>/SKILL.md` and refresh Cowork.

### `copilot-instructions.md`

- **Loaded first at every conversation.** A user-level instruction file at `OneDrive/Documents/Cowork/copilot-instructions.md` is loaded before any skill activates. This is observed behavior, not officially documented; treat it as a working pattern rather than a guaranteed API.
- **High-leverage location.** Reference your `_Compass/` folder here so Cowork consults it for judgment calls. Tell Cowork your defaults: "always draft, never send" or "always show options before recommendations".
- **Separate from M365 Copilot Custom Instructions.** The 8,000-character field in M365 Copilot Settings is platform-wide. `copilot-instructions.md` is Cowork-specific. Use both; they complement.

### Edit-in-Place Limitation

- **Cowork cannot edit files at arbitrary OneDrive paths.** Every output lands in `sessions/`. To "edit" an existing file: upload it, ask Cowork to revise, then manually move the result from `sessions/` to its final home. Cowork is an orchestrator, not an in-place editor.
- **Cannot delete.** Cowork can move files to an Archive folder but cannot permanently delete them. This is a Microsoft safety boundary, not a bug.

For the full set of limits and workarounds, see [`Resources/cowork-limitations.md`](Resources/cowork-limitations.md).

## Who This Is For

You already have Microsoft 365 Copilot Cowork access through your organization. Cowork is currently a Frontier preview, so your org also needs to be enrolled in the [Microsoft Frontier program](https://adoption.microsoft.com/en-us/copilot/frontier-program/). If you do not see Cowork in the Microsoft Admin Center under Agent management, your admin account needs to enroll in Frontier under `Copilot → Settings → Frontier`. This is not a guide to obtaining access; talk to your IT department for that.

This IS a guide to getting the most out of Cowork once you have it. The patterns here assume you can already create skills, run agents, and connect to your Microsoft Graph.

Audience: smart operators and founders configuring Cowork for real work. Technical enough to follow configuration steps but may not have deep M365 admin experience. Written for someone doing this for the first time.

## Getting Started

1. Open [`Journey/`](Journey/) and read the index, then work through the four step pages in order
2. Browse `Resources/` to ground yourself in what Cowork is (Microsoft Learn + community write-ups)
3. Pull the relevant prompt from `Prompts/` when a journey step tells you to (Step 1 and Step 4 have prompts ready)
4. Adapt the templates and playbooks to your own business context as they land

## Roadmap

This is what I plan to add as I keep using Cowork. No fixed timeline; the order reflects what I expect to need first.

- **First `Playbooks/` entry**: a Support Scaling playbook (Cowork-driven inbox triage, response templates, escalation routing)
- **First `Templates/` entry**: a SKILL.md starter template with the most common YAML frontmatter fields and the prompt structure that has worked best for me
- **More installable skills** in `Skills/`: daily briefing, weekly review, meeting prep, deep research framing
- **Screenshots** in Journey Step 1 and Step 3 (Frontier enrollment screen, skill verification slash command)
- **A short troubleshooting guide** in `Resources/` for the most common Cowork failure modes I have hit

See [CHANGELOG.md](CHANGELOG.md) for what has already shipped.

## Contributing

This is a living project. If you are building on Copilot Cowork and have patterns worth sharing, open an issue or PR. Opinionated contributions that ship working examples are preferred over theoretical suggestions.

## License

[MIT](LICENSE)

## Author

Gary Wong ([@Gfriend997](https://github.com/Gfriend997))