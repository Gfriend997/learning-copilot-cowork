# Step 4: Build the Thinking Layer

**Prompt:** [`Prompts/CoWork_Compass_Builder_Prompt_v3.md`](../Prompts/CoWork_Compass_Builder_Prompt_v3.md)

## Why Last

Steps 1 through 3 cover what Cowork knows (Personalization, OneDrive) and what Cowork does (Custom Skills). Step 4 covers how Cowork thinks.

Your Compass folder (created in your OneDrive at `OneDrive/Documents/Cowork/_Compass/`, with the underscore prefix so it sorts above the Cowork-managed `skills/` and `sessions/` folders) holds your decision heuristics, tradeoff rules, escalation criteria, and working style. This is the layer that turns a competent agent into a coworker who can argue with you and be right.

This repo does not ship a sample Compass. It is personal to each user. You build yours by running the Compass Builder prompt below.

This is the highest-leverage step. It is also the hardest to do well. Plan for two passes: a quick first draft to get something working, then a refined second pass after you have used Cowork for a week of real work.

## What Compass Is

A normal AI assistant tells Cowork what to do (skills) and who you are (personalization). Compass tells Cowork **how to think when there is no clear answer.**

Compass files capture:

- **Decision principles.** "When forced to choose between speed and quality, default to speed unless the audience is regulated or external."
- **Tradeoff rules.** "Always show options plus a recommendation. Never just the recommendation. The reasoning matters more than the conclusion."
- **Escalation criteria.** "Stop and ask me before sending anything to legal counsel, the board, or a customer over $100K ARR."
- **Working style.** "I think fastest in writing. Send me bullet points, not paragraphs. Save the narrative for the final draft."

The Compass Builder Prompt interviews you to extract these patterns and writes them as Markdown files. Most users end up with 5 to 8 files: `DECISION_PLAYBOOK`, `WORKING_STYLE`, `WHEN_TO_ESCALATE`, `PRODUCT_HEURISTICS`, `STAKEHOLDER_MAP`, `METRICS_AND_SCORECARDS`, and similar. Your exact file set depends on how you answered.

## Wire Compass into copilot-instructions.md

At the end of the Compass Builder interview, the prompt outputs a snippet you paste into `OneDrive/Documents/Cowork/copilot-instructions.md`. The snippet does NOT dump every Compass file at session start. It loads only the distilled essence (working style, decision principles, stakeholders, current role) and tells Cowork *when* to fetch a specific Compass file on demand.

This lazy-load pattern matters. `copilot-instructions.md` has a roughly 200-line soft cap (see [Guide: copilot-instructions.md](../Resources/copilot-instructions-guide.md)), and you do not want every Compass file inlined there. Load the index; fetch the detail when relevant.

A pattern that works (adapt the file names to whatever your Compass Builder produced):

```markdown
## Compass: the judgment layer

The full Compass lives in OneDrive at `OneDrive/Documents/Cowork/_Compass/`. The distilled essence is loaded here: working style, decision principles, stakeholders, key metrics, current role.

**Fetch a specific Compass file when:**
- A decision is ambiguous and a recommendation is needed -> `DECISION_PLAYBOOK`
- Multiple priorities are in tension -> `DECISION_PLAYBOOK`
- A draft, recommendation, or message is being prepared in my voice -> `WORKING_STYLE`
- A risk, escalation trigger, or red line is in play -> `WHEN_TO_ESCALATE`
- A product or launch readiness call is on the table -> `PRODUCT_HEURISTICS`
- Stakeholders disagree or a cross-group call is needed -> `STAKEHOLDER_MAP`
- A metric, evidence bar, or "what counts as a signal" question -> `METRICS_AND_SCORECARDS`
- About to ask me a question the Compass could answer

**Precedence:** When the Compass conflicts with generic Cowork guidance, the Compass wins. It is the more specific, more recent, user-authored layer.
```

The structure to keep, regardless of your exact file names:

1. **One line saying where the full Compass lives** (the OneDrive path)
2. **A short list of what is auto-loaded** (the essence)
3. **A `Fetch when:` list mapping triggers to specific Compass files** (the lazy-load index)
4. **An explicit precedence rule** (Compass wins over generic Cowork guidance)

That four-part structure is what makes Cowork actually consult your Compass instead of guessing.

## Checklist

- [ ] Open a fresh Cowork chat (no prior context)
- [ ] Upload [`Prompts/CoWork_Compass_Builder_Prompt_v3.md`](../Prompts/CoWork_Compass_Builder_Prompt_v3.md)
- [ ] Ask Cowork to run the Compass Builder interview
- [ ] Answer the questions; expect the interview to take 30 to 45 minutes for the full pass
- [ ] Save the generated Compass files to `OneDrive/Documents/Cowork/_Compass/` (sibling to the `skills/` and `sessions/` folders described in [The Cowork Folder in OneDrive](../Resources/cowork-folder-structure.md); the leading underscore keeps it sorted to the top of the Cowork file browser)
- [ ] Paste the wiring snippet (output at the end of the Compass Builder run) into `OneDrive/Documents/Cowork/copilot-instructions.md`. The snippet follows the four-part structure described in **Wire Compass into copilot-instructions.md** above: full-Compass path, essence list, fetch-when triggers, precedence rule. Do NOT inline every Compass file's contents; the lazy-load pattern is the point.
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

## What You Have After This Step

- A `OneDrive/Documents/Cowork/_Compass/` folder populated with your decision principles
- Custom Instructions in Copilot that reference the Compass folder
- Cowork producing outputs that feel like *you would have written them*, not "generic professional"
- A clear sense of which Compass files need refinement after one week of use

## Beyond the Journey

Once these four steps are in place, you have a working Cowork system. Maintenance from here is incremental:

- Re-run the Personalization Interview quarterly ([Step 1](01-personalize-copilot.md))
- Add custom skills as new repeatable patterns emerge ([Step 3](03-build-custom-skills.md))
- Update Compass files when your priorities shift (this step, refinement pass)
- Watch [`Resources/`](../Resources/) for new Microsoft Learn updates