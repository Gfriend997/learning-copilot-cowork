# Changelog

What has shipped in this repo. Newest at the top. Dates are when the change was committed, not when it was first written or tested.

## 2026-05-21

### Added
- `videos/the-cowork-blueprint.mp4`: a community-contributed walkthrough of the repo and how the pieces fit together. Linked from the new "Video Walkthrough" section at the top of the README.

## 2026-05-18

### Added
- Four-step setup journey, one page per step (`Journey/01` through `Journey/04`)
- Three runnable prompts in `Prompts/`:
  - Copilot Personalization Interview (Step 1)
  - OneDrive Cleanup Prompt with scope selection (Step 2)
  - CoWork Compass Builder v3 (Step 4)
- One installable skill in `Skills/`: GitHub Skill Importer (`skill-05-import-github-skill`)
- Four reference docs in `Resources/`:
  - The Cowork Folder in OneDrive
  - Cowork Limitations and Workarounds
  - Guide: copilot-instructions.md
  - Skills: Capacity and Loading
- Microsoft Learn link, three community deep-dive links, and two Claude Code skill library links in `Resources/`
- README sections: Why This Exists, What Is Copilot Cowork, Async and Cloud-Native, Three Layers (One Coworker), What You Will Find Here, Key Concepts, Cowork Conventions and Nuances, Who This Is For, Getting Started, Roadmap, Contributing
- This CHANGELOG

### Notable refactors
- Folder rename: removed `_` prefix from all top-level repo folders (`_Compass` → `Compass`, etc.). The underscore convention still applies in OneDrive (where Cowork sorts underscored folders to the top); it just does not apply in this repo.
- Path normalization: all OneDrive references now use `OneDrive/Documents/Cowork/...` prefix for clarity
- Compass casing: aligned all docs to `_Compass/` (underscore prefix) to match the Compass Builder prompt's default
- Removed the email-reorganization step from the journey (the cleanup prompt covers email-adjacent organization sufficiently)
- Removed Gary's personal Compass folder contents from the public repo (the Compass concept stays; the personal files do not)
- Removed v1 and v2 of the Compass Builder; v3 is the only one anyone should run

### Placeholders
- `Templates/` and `Playbooks/` folders exist but are empty. See the Roadmap in README for what's coming.

## 2026-05-19

### Added
- `FAQ.md` at repo root. First entry: how to schedule a recurring task in Cowork (tune prompt, append scheduling line, activate the draft).
- All folder entries in README "What You Will Find Here" are now clickable links.

### Fixed
- "Three Layers, One Coworker" section renamed to "Four Layers, One Coworker" (the math was off; section lists four items, including the foundation).
