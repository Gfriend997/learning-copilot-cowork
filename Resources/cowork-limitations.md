# Cowork Limitations and Workarounds

What Cowork cannot do, and how to work around each constraint. Knowing these up front saves hours of frustration. The most consequential one is first.

## Cannot Edit Files In Place

Cowork cannot write or edit a file at an arbitrary location in OneDrive or SharePoint. Every file Cowork creates or modifies lands in `/Documents/Cowork/sessions/`, not at the source location.

**The edit workflow:**

1. Upload the file you want to edit into the Cowork chat (drag and drop, or use the attachment button).
2. Ask Cowork to make the changes.
3. Cowork creates a new version of the file. The output appears in the side panel's **Output folder** during the chat, and is saved permanently to `/Documents/Cowork/sessions/`.
4. To replace the original, you manually move or copy the edited version from `sessions/` to wherever the source lived.

**Why this matters for your workflow:**

- Do not expect "edit my Q3 report" to update the file at its original SharePoint location. It will not.
- For high-frequency edits, build the editing step into a custom skill that documents the manual move-back as the last instruction.
- If you need true in-place editing, use Microsoft 365 Copilot directly inside the Office app (Word, Excel, PowerPoint). Cowork is for multi-step orchestration, not single-document editing.

## Cannot Access Local Files

Cowork only sees files in OneDrive and SharePoint. Files on your local C: drive are invisible.

**Workaround:** upload the file as an attachment to the Cowork chat. Cowork can then work with it. The output, as above, lands in `sessions/`.

## Cannot Delete Files

By design, Cowork cannot permanently delete files in OneDrive or SharePoint. This is a hard Microsoft safety boundary.

**Workaround:** create an `Archive/` folder somewhere in OneDrive. Have Cowork move files there instead of "deleting" them. You can clean up the archive manually on your own schedule.

## Cannot Read Encrypted Files

Files protected by DRM, IRM, or Microsoft Purview encryption are invisible to Cowork even when you have permission to read them.

**Workaround:** decrypt the file first (if your policy permits), upload it, work with it, then re-protect the result if needed. If decryption is not allowed, Cowork is not the right tool for that document.

## Hard Limits to Know

| Limit | Cap |
|---|---|
| Custom skills per user | 50 |
| Size per `SKILL.md` file | 1 MB |
| Companion files per skill | 20 files, 10 MB total |
| Custom Instructions field (M365 Copilot) | 8,000 characters |
| Attachment size per upload | 200 MB |
| Scheduled prompts per user | 5 |
| Chat input length | 250,000 characters |

## Custom Skills Are Not Validated

Microsoft does not review the contents of `SKILL.md` files you create. If a skill produces wrong output, that is on you to catch. Review outputs from every new skill for the first three to five runs before trusting it.

## Practical Design Implication

The edit-in-place limitation shapes how you should think about Cowork:

- Cowork is an **orchestrator**, not an in-place editor. It coordinates multi-step work across apps and produces deliverables.
- For deliverables you want to keep, plan for a "promote from `sessions/` to its final home" step. Some users build this into a skill; some do it manually.
- The `sessions/` folder grows over time. It is fine to leave old session outputs there; they serve as a record of what Cowork has done.
