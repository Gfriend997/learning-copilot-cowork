# Resources

External references, research, and links that support the rest of the repo. The Microsoft Learn docs are the canonical source of truth. Community write-ups add context and perspective.

## Microsoft Official

- [Cowork overview (Microsoft Learn)](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/) - The canonical product documentation. Covers skills, plugins, custom skill format, limitations, security model, and admin controls. Read first.
- [Copilot Cowork: A new way of getting work done](https://www.microsoft.com/en-us/microsoft-365/blog/2026/03/09/copilot-cowork-a-new-way-of-getting-work-done/) - Microsoft 365 Blog, March 2026. Original announcement.
- [Copilot Cowork: From conversation to action across skills, integrations, and devices](https://www.microsoft.com/en-us/microsoft-365/blog/2026/05/05/copilot-cowork-from-conversation-to-action-across-skills-integrations-and-devices/) - Microsoft 365 Blog, May 2026. Expansion update covering plugins and device reach.

## Community Deep-Dives

- [Copilot Cowork: A new way of getting work done in Microsoft 365](https://futurework.blog/2026/04/19/copilot-cowork-a-new-way-of-getting-work-done-in-microsoft-365/) - Future Work blog, April 2026. Strong "what does this actually mean for users" framing, with concrete examples.
- [Claude Cowork vs Copilot Cowork](https://datasciencedojo.com/blog/claude-cowork-vs-copilot-cowork/) - Data Science Dojo. Useful for understanding what Cowork is by contrast with Anthropic's standalone Cowork.

## In This Folder

- [**The Cowork Folder in OneDrive**](cowork-folder-structure.md) - Canonical reference for the `/Documents/Cowork/` subtree: `copilot-instructions.md`, `skills/`, `sessions/`. Read this before Journey Step 2.
- [**Cowork Limitations and Workarounds**](cowork-limitations.md) - What Cowork cannot do (edit files in place, delete, read encrypted files, etc.) and the workaround for each. The edit-in-place constraint shapes how you should think about Cowork.

## Skill Libraries (for inspiration)

If you do not know what custom Cowork skill to build first, browse these public libraries of Claude Code skills. Combined with the [`skill-05-import-github-skill`](../Skills/skill-05-import-github-skill.md) importer (in [`Skills/`](../Skills/)), you can convert any of these into a Cowork-installable skill, reframed for your role.

- [obra/superpowers](https://github.com/obra/superpowers) - Large curated Claude Code skill library. 18.8k stars at time of writing. Strong coverage of engineering, research, and meta-workflows.
- [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) - "Awesome list" style index of Claude Code skills across domains. 12.4k stars at time of writing. Useful for discovering domain-specific skills.

These are Claude Code skills, not Cowork skills natively. The importer translates the format and reframes for your role.

## Access Requirements

- Microsoft 365 Copilot license
- Microsoft Frontier preview program enrollment
- See [Microsoft Frontier program](https://adoption.microsoft.com/en-us/copilot/frontier-program/)

## Note

This is reference material, not execution guidance. For step-by-step instructions, see `Playbooks/`. For decision rules, see `Compass/`.
