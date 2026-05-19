# The Cowork Folder in OneDrive

Microsoft Copilot Cowork lives at `OneDrive/Documents/Cowork/`. Everything Cowork manages on your behalf is rooted there. Understanding the layout is foundational; the journey steps reference this structure.

## The Top-Level Layout

```
OneDrive/
└── Documents/
    └── Cowork/
        ├── copilot-instructions.md          (loaded first when Cowork starts)
        ├── skills/                          (your custom SKILL.md files)
        └── sessions/                        (Cowork-managed output files; do not touch)
```

## What Each Item Does

### `copilot-instructions.md`

A user-level instruction file that Cowork loads at the start of every conversation. Think of it as your personal system prompt for Cowork specifically. Optional but high-leverage; this is where you tell Cowork your durable behavioral rules.

For the full guide (what to put, what to avoid, limitations, best practices, a minimal example), see [Guide: copilot-instructions.md](copilot-instructions-guide.md).

Quick facts:
- Lives at `OneDrive/Documents/Cowork/copilot-instructions.md`
- Separate from the M365 Copilot Custom Instructions field (which is platform-wide, set in [Journey Step 1](../Journey/01-personalize-copilot.md))
- Observed user behavior, not officially documented by Microsoft; treat as a working pattern, not a guaranteed API

### `skills/`

Where your custom SKILL.md files live. One subfolder per skill.

```
Cowork/
└── skills/
    ├── weekly-report/
    │   └── SKILL.md
    ├── client-onboarding/
    │   ├── SKILL.md
    │   └── onboarding-checklist-template.docx
    └── meeting-prep/
        └── SKILL.md
```

Cowork discovers everything inside `skills/` at the start of each conversation. See [Journey Step 3](../Journey/03-build-custom-skills.md) for how to build skills, and the [Microsoft Learn page](https://learn.microsoft.com/microsoft-365/copilot/cowork/use-cowork#create-custom-skills) for the official spec.

**Limits:**
- 50 custom skills total per user
- 1 MB per SKILL.md
- Up to 20 companion files per skill (10 MB total per skill)

### `sessions/`

Cowork saves output files from every chat conversation here. This folder is Cowork-managed; do not edit it directly.

- Every conversation that produces a file (a document, a spreadsheet, a PDF) lands here automatically.
- Cowork organizes the contents; renaming or moving files in `sessions/` will confuse it.
- If you want to keep an output file long-term, move a copy somewhere else in OneDrive (your `Projects/` folder, for example). Leave the original in `sessions/` alone.
- Use this folder as evidence of what Cowork has done; do not treat it as your personal workspace.

**Important constraint:** Cowork cannot write or edit a file at any other OneDrive or SharePoint location. Every output Cowork creates lands here in `sessions/`, including edits of files you uploaded. See [Cowork Limitations and Workarounds](cowork-limitations.md) for the edit workflow and other constraints to know.

## Practical Implications

- **When cleaning OneDrive in [Journey Step 2](../Journey/02-clean-onedrive.md):** leave the entire `Cowork/` subtree alone. The cleanup applies to the rest of OneDrive, not Cowork's managed area.
- **When building skills in [Journey Step 3](../Journey/03-build-custom-skills.md):** create new subfolders inside `skills/`, never modify the parent layout.
- **When building the thinking layer in [Journey Step 4](../Journey/04-thinking-layer.md):** decide whether your Compass files live inside `Cowork/` (as a sibling folder to `skills/`) or elsewhere in OneDrive. Either works; what matters is that `copilot-instructions.md` references the location explicitly.

## Cowork Cannot Delete Files

By design, Cowork cannot permanently delete files in OneDrive or SharePoint. It can move them, including into an Archive folder you create. This applies to `sessions/` too: if it grows large, you can move old session folders out, but Cowork itself will never clean them up automatically.