# Step 2: Clean Your OneDrive

**Prompt:** Coming soon. Interim manual checklist below.

**Required reading first:** [The Cowork Folder in OneDrive](../_Resources/cowork-folder-structure.md). Before touching OneDrive, understand the `/Documents/Cowork/` subtree (`copilot-instructions.md`, `skills/`, `sessions/`). The cleanup in this step applies to *everything else in OneDrive*. The Cowork subtree is managed and stays as-is.

## Why This Order

Cowork pulls signal from your OneDrive and SharePoint when answering anything: drafting documents, finding context, suggesting next actions. If your OneDrive is full of "New folder (3)", "Untitled.docx", and "Copy of Copy of Final_v2_real_FINAL", Cowork's outputs reflect that mess.

Clean input determines output quality. Postpone this step and you spend hours fixing low-quality Cowork results that were doomed at the input layer.

## The Leverage Move

Use Cowork itself to clean OneDrive. It can browse your files, rename based on content, propose folder structures, and move files in batches. You approve each batch. This is faster and more thorough than doing it manually.

## Checklist

- [ ] In a fresh Cowork chat, ask: *"Browse my OneDrive root and tell me which folders have unclear or duplicate purposes."*
- [ ] Review what Cowork reports. Confirm anything that surprises you.
- [ ] Ask Cowork to propose a folder structure that fits your work, not Microsoft's defaults. Iterate until it makes sense.
- [ ] Approve the structure, then have Cowork move files in batches. Cowork pauses for approval per batch (sensitive action).
- [ ] Have Cowork rename any files it flags as unclear ("Untitled", "Copy of", "Final_v2_real_FINAL")
- [ ] Create a `/Documents/Cowork/skills/` folder now, even if empty. [Step 4](04-build-custom-skills.md) needs it.
- [ ] Spot-check the result. Open three random folders. If they make sense at a glance, you are done. If not, iterate.

## What Belongs Where

A starting structure that works for most operators:

```
/Documents/
  Cowork/                      -- Cowork-managed (see Cowork folder reference)
    copilot-instructions.md
    skills/
    sessions/
    Compass/                   -- Thinking-layer files (Step 5), optional location
  Projects/                    -- Active project work, one folder per project
  Reference/                   -- Long-lived material: contracts, templates, research
  Archive/                     -- Done work you want to keep findable but out of the way
```

Adapt the non-Cowork folders as needed. The shape that works is the one you will actually maintain.

## Common Pitfalls

- **Do not let Cowork delete files.** Cowork cannot delete files in OneDrive or SharePoint by design (this is a hard Microsoft limit), but it can move them. Use an "Archive" folder if you want them out of sight.
- **Do not reorganize everything at once.** Tackle the top two levels of your OneDrive first. The deep nested folders can wait.
- **Encrypted files are invisible to Cowork.** If you have files under DRM or RMS encryption, Cowork cannot read them. Note their existence but do not waste time prompting Cowork about their contents.

## What You Have After This Step

- A OneDrive root structure you can navigate in seconds
- File names that describe what is inside them
- A `/Documents/Cowork/skills/` folder ready for Step 4
- Cowork can now find relevant context quickly when you ask it anything

When that is true, move to [Step 3: Reorganize Your Email](03-reorganize-email.md).
