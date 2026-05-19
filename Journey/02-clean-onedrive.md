# Step 2: Clean Your OneDrive

**Prompt:** [`Prompts/OneDrive_Cleanup_Prompt.md`](../Prompts/OneDrive_Cleanup_Prompt.md)

**Required reading first:** [The Cowork Folder in OneDrive](../Resources/cowork-folder-structure.md). Before touching OneDrive, understand the `OneDrive/Documents/Cowork/` subtree (`copilot-instructions.md`, `skills/`, `sessions/`). The cleanup in this step applies to *everything else in OneDrive*. The Cowork subtree is managed and stays as-is.

## Why This Order

Cowork pulls signal from your OneDrive and SharePoint when answering anything: drafting documents, finding context, suggesting next actions. If your OneDrive is full of "New folder (3)", "Untitled.docx", and "Copy of Copy of Final_v2_real_FINAL", Cowork's outputs reflect that mess.

Clean input determines output quality. Postpone this step and you spend hours fixing low-quality Cowork results that were doomed at the input layer.

## How the Cleanup Prompt Works

The OneDrive Cleanup Prompt is **safe by design** and runs in two halves:

- **Part 1 (Planning):** Nothing moves. Every decision goes into a numbered Decision Log.
- **Part 2 (Execution):** Only after you review the full recap and approve, the prompt executes the approved moves.

**Hard rules** confirmed up front, one at a time:

1. Never delete (archive only)
2. Skip sensitive and confidential files
3. Plan first, execute later
4. Stop on errors, ask via multiple choice

**Scope choice** lets you pick the size of the sweep:

- Entire OneDrive (60 to 90 min)
- One specific folder (15 to 30 min)
- Multiple specific folders (30 to 60 min)

**Every interaction is multiple-choice.** No open-ended questions. The prompt classifies each file as KEEP, ARCHIVE, TRANSFER, DUPLICATE, UNCLEAR, or SKIP, and queues moves to `Archive/[Past-Role-or-Project]/[Year]/`.

**Deliverables at the end:** a summary report, a proposed folder structure for your current role, and a follow-up list of items it could not classify.

## Checklist

- [ ] Set aside 30 to 60 minutes of focused time (longer for entire-OneDrive sweep)
- [ ] Open a fresh Copilot Cowork chat
- [ ] Upload `OneDrive_Cleanup_Prompt.md` as an attachment, or paste its contents into the chat
- [ ] Ask Cowork to execute the prompt
- [ ] Confirm each of the four hard rules individually (the prompt asks them one at a time)
- [ ] Confirm the cleanup scope: entire OneDrive, one folder, or multiple folders
- [ ] Confirm your current role (auto-loaded from M365 profile) and the inferred past-role map
- [ ] Walk through the folders one by one. Every interaction is multiple-choice. Nothing moves yet.
- [ ] When the planning is complete, review the full Decision Log + planned actions recap
- [ ] If anything looks wrong, ask to revisit specific decision numbers. The prompt updates and re-displays the recap.
- [ ] Give final approval to execute, or export the plan to a Word document for offline review first
- [ ] Watch the execution progress updates. If any move fails, the prompt stops and asks how to proceed.
- [ ] When done, request all three deliverables (summary, folder structure, follow-up list). They land in `OneDrive/Documents/OneDrive-Cleanup-[YYYY-MM-DD]/`

## What Belongs Where

A starting structure that works for most operators, based on the prompt's proposed folder structure output:

```
OneDrive/
└── Documents/
    ├── Cowork/                      -- Cowork-managed (see Cowork folder reference)
    │   ├── copilot-instructions.md
    │   ├── skills/
    │   ├── sessions/
    │   └── _Compass/                -- Thinking-layer files (Step 4)
    ├── Projects/                    -- Active project work, one folder per project
    ├── Reference/                   -- Long-lived material: contracts, templates, research
    └── Archive/                     -- Created by the cleanup prompt; past roles, duplicates, stale items
```

Adapt the non-Cowork folders as needed. The shape that works is the one you will actually maintain.

## Common Pitfalls

- **Trying to clean during a busy hour.** The prompt is interactive. Block 30 to 60 minutes when you can answer questions without interruption.
- **Choosing "entire OneDrive" when you only need one folder.** If you know the problem area, scope it. You can run the cleanup again later for other folders.
- **Skipping the recap.** The final gate exists for a reason. Read the Decision Log before approving execution.
- **Cowork cannot delete.** Even when you "remove" an empty folder via the prompt, sensitive items in OneDrive cannot be permanently deleted by Cowork. See [Cowork Limitations and Workarounds](../Resources/cowork-limitations.md).

## What You Have After This Step

- A OneDrive root structure you can navigate in seconds
- An `Archive/` folder containing prior-role and stale items, organized by role and year
- A summary report documenting every cleanup decision
- A proposed folder structure for your current role (use it as a starting template, adapt as needed)
- A follow-up list of items the prompt could not classify (decide on these yourself when you have time)
- A `OneDrive/Documents/Cowork/skills/` folder ready for Step 3
- Cowork can now find relevant context quickly when you ask it anything

When that is true, move to [Step 3: Build Your First Custom Skills](03-build-custom-skills.md).
