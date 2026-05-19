# Skills

Installable Cowork skills. Each `SKILL.md` here is a working artifact you can drop into your OneDrive `/Documents/Cowork/skills/` folder to extend Cowork's capabilities.

Skills are different from prompts:

- **Prompts** (in [`Prompts/`](../Prompts/)) are pasted into a fresh Cowork chat to run an interview or one-time workflow.
- **Skills** (here) are installed in OneDrive once. Cowork discovers them at the start of every conversation and activates them when your message matches their trigger phrases.

## How to Install a Skill from This Folder

The install procedure is ~30 seconds per skill:

1. **Create the folder.** In your OneDrive, navigate to `/Documents/Cowork/skills/` and create a subfolder named after the skill (for example, `skill-05-import-github-skill/` or `import-github-skill/`. The name is up to you; Cowork uses the `name:` in the YAML frontmatter, not the folder name).
2. **Copy the file.** Save the contents of the corresponding `.md` file from this folder as `SKILL.md` (all caps) inside the new subfolder.
3. **Refresh.** Close and reopen your Cowork chat (or start a new one). Cowork discovers custom skills at conversation start, not mid-conversation.
4. **Verify.** In the prompt window, type `/` and look for the skill in the suggestions list. If it appears, it loaded successfully.

## Contents

### `skill-05-import-github-skill.md`

Imports a Claude Code skill from a public GitHub repository into your Cowork skills library, reframing it for your role and domain.

**Trigger phrases:**
- "Import this skill from [GitHub URL]"
- "Turn this repo into a Cowork skill"
- "Adapt this skill for my domain"

**What it does:** fetches the source SKILL.md or README, asks whether to reframe for your role, drafts a Cowork-format SKILL.md, validates it, and stages an uploadable copy in `/Documents/Cowork/sessions/` for you to drag into your skills folder.

**Why it matters:** combined with the public Claude Code skill libraries (see [Skill Libraries](../Resources/README.md#skill-libraries-for-inspiration) in `Resources/`), this skill turns hundreds of battle-tested community skills into Cowork-installable artifacts. You stop reinventing the wheel.

## After Importing: The Sessions-to-Skills Hop

When the importer (or any Cowork session) generates a new `SKILL.md`, the file lands in `/Documents/Cowork/sessions/`, not directly in `skills/`. This is the Cowork edit-in-place limitation in action (see [Cowork Limitations and Workarounds](../Resources/cowork-limitations.md)).

To make the new skill permanent:

1. Open `/Documents/Cowork/sessions/` and find the newly created file
2. Move (or copy) it into a new subfolder inside `/Documents/Cowork/skills/<your-chosen-name>/`
3. Rename the file to `SKILL.md` if the importer named it something else
4. Refresh your Cowork session to load it

This manual hop is annoying once, then automatic in your muscle memory.

## Contributing Skills

If you build a working skill and want to share it back, open a PR adding the `.md` file to this folder plus a short entry in this README under "Contents." Keep skills outcome-focused: the name should describe what they produce, not how.
