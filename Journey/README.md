# The Cowork Setup Journey

Four steps to go from "I have access" to "Cowork is my second brain." This is the order I would recommend if you were starting today. Not the messy way I arrived at it; the order I wish I had followed.

Each step is a separate page. Work top to bottom. Skipping ahead causes rework.

**Before you start:** Read these two foundational references. They shape every step.

- [The Cowork Folder in OneDrive](../Resources/cowork-folder-structure.md) - the `/Documents/Cowork/` layout (`copilot-instructions.md`, `skills/`, `sessions/`)
- [Cowork Limitations and Workarounds](../Resources/cowork-limitations.md) - what Cowork cannot do (edit files in place, delete, etc.) and how to work around each

## The Steps

1. [**Personalize Copilot**](01-personalize-copilot.md) - Set up Microsoft 365 Copilot Custom Instructions. Cowork inherits this. Foundation for everything else.
2. [**Clean Your OneDrive**](02-clean-onedrive.md) - Cowork pulls signal from OneDrive. Clean input determines output quality. Use Cowork itself to do the cleanup.
3. [**Build Your First Custom Skills**](03-build-custom-skills.md) - Anything you do more than three times a month is a SKILL.md candidate.
4. [**Build the Thinking Layer**](04-thinking-layer.md) - The `Compass/` files: how you think, not just what you do. The highest-leverage step, and the hardest to do well.

## Why This Order

- Steps 1 and 4 are about Cowork's mind: what it knows about you, how it thinks. The bookends.
- Step 2 is the substrate Cowork operates on: a clean OneDrive. Clean substrate, clean output.
- Step 3 sits between because skills only become useful once the substrate is clean and Cowork knows enough about you to write decent first drafts.

Build the foundation before adding the leverage layers. Otherwise the leverage compounds the wrong thing.

## Prompts Used

The journey references prompts in [`Prompts/`](../Prompts/):

- Step 1: [`Copilot_Personalization_Interview.md`](../Prompts/Copilot_Personalization_Interview.md)
- Step 2: [`OneDrive_Cleanup_Prompt.md`](../Prompts/OneDrive_Cleanup_Prompt.md)
- Step 3: [`skill-05-import-github-skill.md`](../Skills/skill-05-import-github-skill.md) (installable importer skill; use with [obra/superpowers](https://github.com/obra/superpowers) and [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) for inspiration)
- Step 4: [`CoWorkCompass_Builder_Prompt_v3.md`](../Prompts/CoWorkCompass_Builder_Prompt_v3.md)
