# The Cowork Setup Journey

Five steps to go from "I have access" to "Cowork is my second brain." Use this file as a checklist. Each step links to the specific prompt in `_Prompts/` that drives it. Work top to bottom; skipping ahead causes rework.

---

## Step 1: Personalize Copilot

**Prompt:** [`_Prompts/Copilot_Personalization_Interview.md`](_Prompts/Copilot_Personalization_Interview.md)

**Why first:** Cowork inherits context from Microsoft 365 Copilot through Work IQ. If your Copilot profile is generic, every Cowork output will be generic. Fix the foundation first.

**Checklist:**

- [ ] Sign in to Copilot at [m365.cloud.microsoft](https://m365.cloud.microsoft)
- [ ] Open Settings, go to **Personalizations**
- [ ] Turn on **Save memory** so Copilot accumulates context about you over time
- [ ] Open a fresh Copilot Cowork chat
- [ ] Upload `Copilot_Personalization_Interview.md` as an attachment (or paste its contents)
- [ ] Ask Cowork to execute the prompt
- [ ] Choose **Full mode** (25-30 min, full depth) or **Express mode** (10 min, highest-leverage areas only). Express is the right starting point for most people.
- [ ] Answer the interview questions one at a time
- [ ] Copy the final output (around 5,000 characters) into Settings, Personalizations, **Custom Instructions**
- [ ] Run the three test prompts the interview suggests, to verify the instruction actually changed Cowork's behavior

**Tip:** Save the final instruction text somewhere editable (a OneDrive note or a Compass file). You will want to tune it after a week of real use. Re-run the interview quarterly; roles and audiences drift.

---

## Step 2: Clean Your OneDrive

**Prompt:** Coming soon.

**Why this order:** Cowork pulls signal from your OneDrive and SharePoint when answering anything. If your OneDrive is full of "New folder (3)" and "Untitled.docx", Cowork's outputs reflect that. Clean input determines output quality.

**Checklist (interim, no dedicated prompt yet):**

- [ ] In Cowork, ask: "Browse my OneDrive root and tell me which folders have unclear or duplicate purposes"
- [ ] Have Cowork propose a folder structure that fits your work, not Microsoft's defaults
- [ ] Approve the structure, then have Cowork move files in batches (it will pause for approval per move)
- [ ] Rename any files Cowork flags as unclear ("Untitled", "Copy of", "Final_v2_real_FINAL")
- [ ] Create a `/Documents/Cowork/skills/` folder now, even if empty. Step 4 needs it.

---

## Step 3: Reorganize Your Email

**Prompt:** Coming soon.

**Why this order:** A clean inbox unblocks your day. Cowork can produce a meaningful daily briefing only after the inbox represents reality, not three weeks of accumulated noise.

**Checklist (interim, no dedicated prompt yet):**

- [ ] Ask Cowork to triage your inbox: archive done items, surface needs-response, schedule calendarables, delete noise
- [ ] Approve actions in batches (Cowork pauses for medium and high risk actions)
- [ ] Have Cowork suggest folder/category rules for recurring senders or topics
- [ ] Set up a daily briefing: "Send me a daily briefing every weekday at 8 AM covering yesterday's done items, today's meetings, and three top priorities"
- [ ] Confirm the briefing appears the next morning. If not, check the **Scheduled** tab in the Cowork side panel.

---

## Step 4: Build Your First Custom Skills

**Prompt:** Coming soon (SKILL.md template + "what to skill" decision rule).

**Why this order:** Building skills before context is clean produces brittle skills that compensate for messy inputs. Building skills after Step 2 and 3 means each skill draws from real signal.

**Checklist:**

- [ ] List every task you do more than three times in a month
- [ ] For each, ask: would a SKILL.md save me 15 minutes or more per run? If yes, candidate.
- [ ] Pick one candidate to start. Resist the urge to build five at once.
- [ ] Create a subfolder under `/Documents/Cowork/skills/<your-skill-name>/`
- [ ] Create `SKILL.md` inside it with YAML frontmatter (`name:`, `description:`) and instructions in plain Markdown
- [ ] Open a fresh Cowork chat. Cowork discovers custom skills at conversation start.
- [ ] Trigger the skill ("Run my weekly report skill"). Verify output.
- [ ] Tune the SKILL.md based on what Cowork got wrong. Re-run.
- [ ] Repeat for the next candidate. Cap at 50 custom skills per user (Microsoft's limit).

**Limits to know:** 50 custom skills total, 1 MB per SKILL.md, up to 20 companion files per skill (10 MB total per skill).

---

## Step 5: Build the Thinking Layer

**Prompt:** [`_Prompts/CoWork_Compass_Builder_Prompt_v3.md`](_Prompts/CoWork_Compass_Builder_Prompt_v3.md)

**Why last:** Steps 1 through 4 cover what Cowork knows and does. Step 5 covers how Cowork thinks. The `_Compass/` folder holds your decision heuristics, tradeoff rules, escalation criteria, and working style. This is what turns a competent agent into a coworker.

**Checklist:**

- [ ] Open a fresh Cowork chat
- [ ] Upload `CoWork_Compass_Builder_Prompt_v3.md`
- [ ] Ask Cowork to run the Compass Builder interview
- [ ] Answer the questions; expect the interview to take 30-45 minutes for the full pass
- [ ] Save the generated Compass files to `/Documents/Cowork/Compass/` (or wherever the prompt directs)
- [ ] Reference the Compass folder explicitly in your Copilot Custom Instructions ("When making decisions, consult my Compass folder at...")
- [ ] Test: ask Cowork a question that requires judgment, not just retrieval. Verify it pulls from the Compass.

**Tip:** Compass is the highest-leverage step but also the hardest to do well. Plan for two passes: a quick first draft to get something working, then a refined second pass after you have used Cowork for a week with real work.

---

## Beyond the Journey

Once these five steps are in place, you have a working Cowork system. Maintenance from here is incremental:

- Re-run the Personalization Interview quarterly
- Add custom skills as new repeatable patterns emerge
- Update Compass files when your priorities shift
- Watch the [`_Resources/`](_Resources/) folder for new Microsoft Learn updates

Each "Coming soon" prompt in this file will be filled in as I build the corresponding playbook. Watch `_Playbooks/` and `_Prompts/` for additions.
