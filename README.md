# Learning Copilot Cowork

A public learning journal and practical blueprint for configuring Microsoft 365 Copilot Cowork (Agentic Wave 3) for real work.

This is not a feature overview or product review. It is a working notebook from someone configuring this system day-to-day, sharing the patterns that hold up and the ones that do not.

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
- **OS-level reach**: operates across local files, Outlook, Teams, and OneDrive in a single workflow
- **Custom skills**: user-defined workflows as `SKILL.md` files in OneDrive at `/Documents/Cowork/skills/`, up to 50 skills per user, no code required

The configuration leverage point is the last one. **Custom skills plus how you structure your Microsoft Graph determine the quality of every output.** This repo is about that leverage.

## What You Will Find Here

**`_Compass/`** - The judgment layer. Decision principles, working style, product heuristics, and escalation rules. The pattern that turns a generic AI assistant into one that thinks like you do.

**`_Templates/`** - Reusable document and workflow templates. Coming soon.

**`_Playbooks/`** - Structured guides for specific project types: Support Scaling, Venture Launch, Community Management, and more. Coming soon.

**`_Resources/`** - External references and links: Microsoft Learn docs, Microsoft announcement blogs, community deep-dives. Start here if you are new to Cowork.

**Builder Prompts** - The prompts I use to bootstrap Cowork. The version history is part of the learning journey:
- `Copilot_Cowork_Operating_System_Builder_Prompt.md` (v1, original)
- `CoWork_OS_Builder_Prompt_v2.md` (v2, refined)
- `CoWork_Compass_Builder_Prompt_v3.md` (v3, current)

**`_OperatingSystem_Guide.docx`** - Original guide explaining the Operating System concept that evolved into `_Compass/`.

## Key Concepts

**The Operational Brain** - SharePoint and OneDrive are not just file storage. They are Cowork's knowledge layer. How you structure them determines the quality of everything Cowork produces.

**Context Fencing** - If you run multiple businesses or projects, you need architectural patterns that prevent data bleed. Cowork should never pull context from Business A when working on Business B.

**Work IQ** - Cowork's reasoning capability improves with better-structured source data, not more data. Quality over quantity, every time.

**The _Compass/ Folder** - Skills tell Cowork what to do. Projects tell Cowork what is happening. The `_Compass/` folder tells Cowork who you are as a leader.

## Who This Is For

You already have Microsoft 365 Copilot Cowork access through your organization. Cowork is currently a Frontier preview, so your org also needs to be enrolled in the [Microsoft Frontier program](https://adoption.microsoft.com/en-us/copilot/frontier-program/). If you do not see Cowork in the Microsoft Admin Center under Agent management, your admin account needs to enroll in Frontier under `Copilot → Settings → Frontier`. This is not a guide to obtaining access; talk to your IT department for that.

This IS a guide to getting the most out of Cowork once you have it. The patterns here assume you can already create skills, run agents, and connect to your Microsoft Graph.

Audience: smart operators and founders configuring Cowork for real work. Technical enough to follow configuration steps but may not have deep M365 admin experience. Written for someone doing this for the first time.

## Philosophy

- AI should augment humans, not replace judgment
- Execution over strategy: ship working systems, not slide decks
- Be opinionated. Neutral guidance gets ignored
- If it cannot be replicated by someone else, it is not a system
- This is a learning journey, not a finished product. Patterns evolve as the system does

## Getting Started

1. Start with the `_Compass/` folder to understand the judgment layer concept
2. Read through the builder prompts to see how the system is bootstrapped
3. Adapt the templates and playbooks to your own business context once they land

## Contributing

This is a living project. If you are building on Copilot Cowork and have patterns worth sharing, open an issue or PR. Opinionated contributions that ship working examples are preferred over theoretical suggestions.

## License

[MIT](LICENSE)

## Author

Gary Wong ([@Gfriend997](https://github.com/Gfriend997))
