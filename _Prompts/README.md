# Prompts

Reusable prompt files for bootstrapping and tuning Microsoft Copilot Cowork. Each prompt is a self-contained Markdown file you upload (or paste) into a fresh Cowork chat.

## Contents

### Personalization

- **`Copilot_Personalization_Interview.md`** - Builds your Microsoft 365 Copilot custom instructions through an adaptive interview. Auto-loads your work profile, tailors questions to your role (engineer / sales / exec / etc.), and outputs a copy-paste-ready custom instruction within Copilot's 8,000 character ceiling. Used in [Journey Step 1](../_Journey/01-personalize-copilot.md).

### Cleanup

- **`OneDrive_Cleanup_Prompt.md`** - Reorganizes your OneDrive around your current role. Safe by design (never deletes, archive-only). Plan-then-execute flow with a full Decision Log and recap. Lets you scope the sweep: entire OneDrive, one folder, or a specific set. Multiple-choice questions only. Used in [Journey Step 2](../_Journey/02-clean-onedrive.md).

### Compass Builders (Versioned)

The Compass folder is Cowork's judgment layer. These prompts interview you and generate the `_Compass/` files. Three versions are kept so the evolution of the approach is visible.

- **`CoWork_Compass_Builder_Prompt_v3.md`** - Current. Used in [Journey Step 4](../_Journey/04-thinking-layer.md).
- **`CoWork_OS_Builder_Prompt_v2.md`** - Predecessor. Branded "OS" before the rename to Compass.
- **`Copilot_Cowork_Operating_System_Builder_Prompt.md`** - First version. Conceptual origin.

For why the v3 is current and what changed, see the prompts themselves; the version history is part of the learning journey.

## How to Use

1. Open a fresh Cowork chat (no prior context).
2. Upload the relevant prompt file as an attachment, or paste its contents into the message.
3. Tell Cowork to execute it.
4. Answer the interview questions.
5. Copy the final output into the destination noted at the top of the prompt (Copilot Custom Instructions field, OneDrive Compass folder, etc.).
