# Step 5: Build the Thinking Layer

**Prompt:** [`_Prompts/CoWork_Compass_Builder_Prompt_v3.md`](../_Prompts/CoWork_Compass_Builder_Prompt_v3.md)

## Why Last

Steps 1 through 4 cover what Cowork knows (Personalization, OneDrive, Email) and what Cowork does (Custom Skills). Step 5 covers how Cowork thinks.

The `_Compass/` folder holds your decision heuristics, tradeoff rules, escalation criteria, and working style. This is the layer that turns a competent agent into a coworker who can argue with you and be right.

This is the highest-leverage step. It is also the hardest to do well. Plan for two passes: a quick first draft to get something working, then a refined second pass after you have used Cowork for a week of real work.

## What Compass Is

A normal AI assistant tells Cowork what to do (skills) and who you are (personalization). Compass tells Cowork **how to think when there is no clear answer.**

Compass files capture:

- **Decision principles.** "When forced to choose between speed and quality, default to speed unless the audience is regulated or external."
- **Tradeoff rules.** "Always show options plus a recommendation. Never just the recommendation. The reasoning matters more than the conclusion."
- **Escalation criteria.** "Stop and ask me before sending anything to legal counsel, the board, or a customer over $100K ARR."
- **Working style.** "I think fastest in writing. Send me bullet points, not paragraphs. Save the narrative for the final draft."

The Compass Builder Prompt interviews you to extract these patterns and writes them as Markdown files.

## Checklist

- [ ] Open a fresh Cowork chat (no prior context)
- [ ] Upload [`_Prompts/CoWork_Compass_Builder_Prompt_v3.md`](../_Prompts/CoWork_Compass_Builder_Prompt_v3.md)
- [ ] Ask Cowork to run the Compass Builder interview
- [ ] Answer the questions; expect the interview to take 30 to 45 minutes for the full pass
- [ ] Save the generated Compass files to `/Documents/Cowork/Compass/` (sibling to the `skills/` and `sessions/` folders described in [The Cowork Folder in OneDrive](../_Resources/cowork-folder-structure.md))
- [ ] Reference the Compass folder in `/Documents/Cowork/copilot-instructions.md` so Cowork loads it at the start of every conversation. Example line: *"When making decisions, consult my Compass folder at /Documents/Cowork/Compass/. Treat those files as authoritative for how I think."*
- [ ] Also add the same reference to your Microsoft 365 Copilot Custom Instructions (from [Step 1](01-personalize-copilot.md)) for cases where Cowork is not the entry point
- [ ] Test: ask Cowork a question that requires judgment, not just retrieval. Verify it pulls from the Compass and references specific principles.
- [ ] Use Cowork normally for a week. Note any time it gives an answer that contradicts how you would think.
- [ ] Run the Compass Builder again as a refinement pass. Update or add the files that needed work.

## Why Two Passes

The first pass captures your stated preferences. The second pass captures your revealed preferences (what you actually do when Cowork gets it wrong).

Most people discover during the second pass that their stated preferences and revealed preferences diverge by 20 to 30 percent. That gap is where Compass becomes valuable. The stated preferences are easy. The revealed preferences are where Cowork starts feeling like it actually knows you.

## Common Pitfalls

- **Skipping the second pass.** First-pass Compass is generic. Real value comes from the refinement.
- **Treating Compass like documentation.** It is not a wiki. It is instructions to Cowork. Write it in second person ("You should...", "When deciding...").
- **Trying to capture every principle.** Cover the top 10 to 15 decisions you make often. Skip the once-a-year edge cases.
- **Not referencing Compass from Custom Instructions.** Compass files in OneDrive are inert unless Cowork knows to consult them. Step 1's Custom Instructions need to point at the Compass folder explicitly.
- **Letting Compass drift.** When your priorities shift (new role, new business, new audience), re-run the Compass Builder. Stale Compass is worse than no Compass; it produces confident wrong answers.

## The Version History in `_Prompts/`

The repo keeps three versions of the Compass Builder:

- `CoWork_Compass_Builder_Prompt_v3.md` (current, recommended)
- `CoWork_OS_Builder_Prompt_v2.md` (predecessor, when this was called "OS")
- `Copilot_Cowork_Operating_System_Builder_Prompt.md` (first version, conceptual origin)

Use v3. The older versions are kept so you can see how the approach evolved. If you read them in reverse order (v1 → v2 → v3), you see the questions that mattered most and the ones that were noise.

## What You Have After This Step

- A `/Documents/Cowork/Compass/` folder populated with your decision principles
- Custom Instructions in Copilot that reference the Compass folder
- Cowork producing outputs that feel like *you would have written them*, not "generic professional"
- A clear sense of which Compass files need refinement after one week of use

## Beyond the Journey

Once these five steps are in place, you have a working Cowork system. Maintenance from here is incremental:

- Re-run the Personalization Interview quarterly ([Step 1](01-personalize-copilot.md))
- Add custom skills as new repeatable patterns emerge ([Step 4](04-build-custom-skills.md))
- Update Compass files when your priorities shift (this step, refinement pass)
- Watch [`_Resources/`](../_Resources/) for new Microsoft Learn updates
