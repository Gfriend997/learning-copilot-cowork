# OneDrive Cleanup Prompt

A reusable Copilot Cowork prompt for organizing your OneDrive around your current role. Safe by design: **nothing is ever deleted**, only moved to an archive folder for review. Copilot walks you through everything as a series of **multiple-choice questions**, captures every decision in a running log, and shows you a complete recap before any file is moved.

You choose the scope at the start: the entire OneDrive, a single folder, or a specific set of folders.

---

## How to Use

1. Copy the prompt below (everything between the `---` markers).
2. Paste it into a new Copilot Cowork chat.
3. Confirm the four hard rules and pick your cleanup scope.
4. Pick from the multiple-choice options as Copilot walks you through your scoped area folder by folder. **Nothing happens to your files yet, this is the planning phase.**
5. Review the full decision recap when prompted, and give the final go-ahead.
6. Copilot then executes the approved moves and produces your summary report, proposed structure, and follow-up list.

Best run when you have 30 to 60 minutes of focused time. You can also stop partway and resume later.

---

## The Prompt

```
Help me clean up and reorganize my OneDrive so it reflects my current role
and active work. Follow this process carefully and never skip steps.

The flow has two halves:
  PART 1 - PLANNING: We make all decisions together. Nothing moves yet.
  PART 2 - EXECUTION: After I see the full recap and approve, you carry
                      out the approved actions.

# Interaction style (very important)

Whenever you need input from me, ALWAYS ask using a multiple-choice
question with 2 to 4 clearly-labeled options. Do not ask open-ended
questions. If I genuinely need a free-text answer, include "Something
else (let me describe)" as one of the choices and only then accept
free text.

Examples of how to ask:
  - "How should I handle these 12 files from your old Marketing role?"
      A) Archive them all to Archive/Marketing-2019-2021/[Year]/
      B) Archive some, keep some, let me review one by one
      C) Transfer to current Marketing team (I'll suggest who)
      D) Skip this folder for now
  - "This folder name 'New Folder (3)' is unclear. What do you want?"
      A) Rename to: [your suggestion]
      B) Leave the name alone
      C) Let me type a new name

Never ask me to confirm with vague phrasing like "Does that work?" or
"Proceed?". Always give me labeled choices.

# Decision logging (do this throughout)

Maintain a running "Decision Log" from the very first question.
For every multiple-choice question you ask me, record:
    #  | Phase | Question | Options shown | My answer | Resulting action
Number entries sequentially (1, 2, 3 ...) so they can be referenced
later. Treat the log as the source of truth: every action you
execute later must trace back to a numbered decision.

# Hard rules (confirm each rule separately before starting)

Present each of the four hard rules to me one at a time, as its own
multiple-choice question. Do NOT bundle them together. Each rule
must be confirmed individually so I know exactly what I'm agreeing
to and what the resulting behavior will be. Record each answer in
the Decision Log as decision #1, #2, #3, #4.

After all four are confirmed, show me a brief recap of the four
choices and ask one final "Ready to begin the cleanup?" question
before moving to Phase 1.

---

RULE 1 OF 4 - Deletion policy

  "Rule 1: I will NEVER delete any file or folder during this cleanup.
   The only action on files marked for cleanup is to MOVE them into an
   'Archive/' folder inside your OneDrive. Confirm this rule?"
     A) Confirm: never delete anything, archive only (recommended)
     B) Allow deletion only for empty folders after archiving
     C) Allow deletion with my explicit confirmation each time
     D) Cancel the cleanup

---

RULE 2 OF 4 - Sensitive and confidential files

  "Rule 2: I will NEVER touch files flagged as sensitive or confidential.
   This includes: files with sensitivity labels (Confidential, Restricted,
   etc.), files under legal hold, files in folders named after legal/HR/
   finance/compliance topics, and files containing obvious PII or
   regulated data. If unsure, I will treat as sensitive and skip.
   Confirm this rule?"
     A) Confirm: skip all sensitive/confidential files (recommended)
     B) Confirm, AND add custom folder names I should always skip
        (you'll list them next)
     C) Loosen: only skip files with formal sensitivity labels
     D) Cancel the cleanup

---

RULE 3 OF 4 - Plan first, execute later

  "Rule 3: All file moves will happen in a single execution pass AFTER
   you review the full Decision Log and give final approval. The
   folder-by-folder questions in Part 1 are PLANNING ONLY: they record
   your intent in the Decision Log; they do not move any file yet.
   Confirm this rule?"
     A) Confirm: plan everything first, then one final approval to
        execute (recommended)
     B) Hybrid: let me approve and execute folder by folder as we go
     C) Auto-execute after each folder once I approve that folder
     D) Cancel the cleanup

---

RULE 4 OF 4 - Error handling

  "Rule 4: If a tool call fails or returns unclear results, I will stop
   and ask you (via multiple choice) how to proceed. I will NOT guess
   at file paths or invent files. Confirm this rule?"
     A) Confirm: always stop and ask on errors (recommended)
     B) Confirm, but retry once silently before asking
     C) Skip failed files silently and add them to the follow-up list
     D) Cancel the cleanup

---

After all four rules are answered, display the recap:

    ============================================================
    HARD RULES - YOUR CONFIRMED CHOICES
    ============================================================
    Rule 1 (Deletion):       Your answer: [letter] - [text]
    Rule 2 (Sensitive files): Your answer: [letter] - [text]
    Rule 3 (Plan vs execute): Your answer: [letter] - [text]
    Rule 4 (Errors):          Your answer: [letter] - [text]
    ============================================================

Then ask:

    "These are the ground rules for the cleanup. Ready to begin?"
       A) Yes: start Phase 1
       B) Change one of the rule answers (tell me which number)
       C) Cancel the cleanup

If I pick (B), re-ask the specific rule question, update the log,
re-display the recap, and ask "Ready to begin?" again. Loop until
I pick (A) or (C).

# PART 1 - PLANNING

## Phase 1 - Establish role context and scope

1. Look up my current role from my M365 profile (job title, team,
   manager, recent collaborators). Tell me what you found and ask:
       "Is this an accurate description of your current role?"
         A) Yes, accurate: use this as my current role
         B) Mostly right, but I want to add current projects
         C) Out of date: let me describe my current role

2. Scan my OneDrive at a high level (folder names, top-level structure,
   modification dates) and INFER my likely past roles, major past
   projects, and approximate time periods. Present this as a draft
   list, for example:
       - 2019-2021: Marketing Analyst (folders: "Campaigns-2019",
         "Q4-Launch", "Brand-Refresh")
       - 2021-2023: Product Manager (folders: "PM-Notes",
         "Roadmap-2022", "Feature-Specs")
       - 2023-present: [current role from profile]
   Then ask:
       "Does this past-role map look right?"
         A) Yes, all correct: proceed
         B) Mostly right: let me correct one or two items
         C) Add a role or project I'm missing
         D) Redo from scratch: let me list them

3. Lock in the confirmed role map.

4. Confirm the cleanup scope before scanning further. Ask:
       "How much of your OneDrive do you want to clean in this session?"
         A) Entire OneDrive (top-down from the root, every folder)
         B) One specific folder (I'll tell you which one)
         C) Multiple specific folders (I'll list them)
         D) Cancel the cleanup

   - If I pick (A), the scope is my OneDrive root. Walk every top-level
     folder in Part 2.
   - If I pick (B), ask:
         "Which folder? Type the path, for example /Documents/Old-Projects/"
     Confirm the path back to me and ask:
         "Confirmed scope: [path]. Proceed?"
           A) Yes
           B) Let me give a different path
           C) Cancel
   - If I pick (C), ask:
         "List the folder paths you want to clean, one per line. I'll
          confirm each before we start."
     Then read the paths back to me in a multiple-choice confirmation:
         "Confirmed scope: [list of paths]. Proceed?"
           A) Yes
           B) Let me edit the list
           C) Cancel

   Record the chosen scope in the Decision Log. The scope determines
   what Phase 2 walks; never expand beyond the confirmed scope without
   explicit re-confirmation.

## Phase 2 - Folder-by-folder planning (no files move yet)

Work top-down through the confirmed scope from Phase 1 step 4, one
folder at a time. Record every decision in the Decision Log. DO NOT
move, rename, or delete anything in this phase, even folder renames
and empty-folder removals are queued for Part 2.

For each folder:

  a. Summarize what's in it: number of files, file types, date range,
     and a one-line description of what the folder appears to be about.

  b. Classify each file (or group of similar files) into one of:
       - KEEP: actively relevant to my current role
       - ARCHIVE (prior role/project): belongs to a past role; queue
         move to Archive/[Role-or-Project-Name]/[Year]/
       - ARCHIVE (stale): untouched > 3 years and no longer relevant;
         queue move to Archive/[Role-or-Project-Name]/[Year-Modified]/
       - TRANSFER CANDIDATE: looks like it belongs to another person
         or team now. Suggest the likely current owner.
       - DUPLICATE: appears to be a near-duplicate of another file.
       - UNCLEAR: can't confidently classify. Add to follow-up list.
       - SKIP: sensitive/confidential (hard rule #2).

  c. Present proposed actions for the whole folder as a single
     multiple-choice question, e.g.:
         "Folder: /Old-Projects/Q3-Launch-2020
          Proposed actions:
            - Archive 14 files to Archive/PM-Role-2020-2022/2020/
            - Flag 2 duplicates for my review
            - Keep 1 file (modified last month)
          What do you want to do?"
            A) Approve all proposed actions (added to plan)
            B) Approve most, but let me change a few
            C) Review file-by-file instead
            D) Skip this folder entirely

  d. If I pick (B) or (C), walk the affected files individually with
     their own multiple-choice (Archive / Keep / Transfer / Skip).

  e. For DUPLICATE groups:
         "Found 3 versions of 'Q3-Report': which to keep?"
           A) Keep [filename-v3.docx] (newest, 2024-11)
           B) Keep [filename-final.docx] (named 'final')
           C) Keep them all
           D) Let me review side by side
     Non-kept versions queue for Archive/Duplicates/[Year]/.

  f. After classifying the folder's contents:
       - If the folder would be empty after the queued moves, ask:
             "Folder will be empty after the planned moves. Queue
              removal of the empty folder?"
               A) Yes, queue removal
               B) No, keep the folder shell
       - If the folder name is messy, ask:
             "This folder's name is unclear. Queue a rename?"
               A) Rename to: [your suggestion]
               B) Leave the name alone
               C) Let me type a new name

Archive folder structure (will be created in Part 2):
  Archive/
    [Past-Role-or-Project-Name]/
      [Year]/
        (files)
    Duplicates/
      [Year]/
        (files)

## Phase 3 - Edge cases (always ask, never assume)

- Files shared with active collaborators:
      "This file is currently shared with [names]. What to do?"
        A) Skip: leave it where it is
        B) Queue archive anyway (sharing link will break)
        C) Notify the collaborators first, then archive
- Files synced from Teams or SharePoint libraries: never queue a move.
  Add to the follow-up list.
- Personal templates, signatures, recurring-use reference files: keep
  regardless of age. If unsure:
      "Looks like a recurring-use file. Treat as a template?"
        A) Yes, keep regardless of age
        B) No, classify normally
- Files in unfamiliar languages or with cryptic filenames: always ask.
- Files outside the confirmed scope: never touch. If a file in scope
  references a file outside scope, note it on the follow-up list.

# PART 2 - REVIEW AND EXECUTE

## Phase 4 - Full recap (mandatory final gate)

When the planning is complete, display the ENTIRE Decision Log to me
on screen in this exact format:

    ============================================================
    ONEDRIVE CLEANUP - REVIEW BEFORE EXECUTING
    ============================================================
    Cleanup scope: [Entire OneDrive | Single folder: <path> |
                    Multiple folders: <list>]
    Total questions asked: [N]
    Total decisions recorded: [N]

    --- ALL QUESTIONS AND ANSWERS ---
    1. [Phase] Question: "..."
       Options shown: A) ...  B) ...  C) ...
       My answer: [letter] - [text]

    2. [Phase] Question: "..."
       Options shown: ...
       My answer: ...

    (continue for every numbered entry)

    --- PLANNED ACTIONS (derived from above) ---
    Files to archive: [count]
       - Archive/Marketing-2019-2021/2020/: [N] files
       - Archive/PM-Role-2021-2023/2022/: [N] files
       - Archive/Duplicates/2024/: [N] files
       (list every destination with file counts)
    Files to transfer: [count]   (list each with suggested recipient)
    Folders to rename: [count]   (list old -> new name)
    Empty folders to remove: [count]   (list each path)
    Files flagged for follow-up: [count]
    Files left untouched: [count]
    ============================================================

After displaying the recap, ask me one final multiple-choice question:

    "This is the complete plan based on every answer above. Ready to
     execute?"
       A) Yes: execute everything as shown
       B) Wait: let me change specific items first (I'll tell you
          which decision numbers to revisit)
       C) Export the plan to a file for me to review offline first
       D) Cancel: don't execute anything

If I pick (B), let me name the decision numbers to revisit, re-ask
those questions, update the log, then re-display the FULL recap and
ask the final question again. Loop until I pick (A), (C), or (D).

If I pick (C), save the recap as a Word document to my OneDrive and
stop. I'll come back later to run execution.

Only when I pick (A), and never before, proceed to Phase 5.

## Phase 5 - Execute

Carry out every queued action from the recap in this order:
  1. Create the Archive/ folder structure as needed
  2. Move files to their archive destinations
  3. Move duplicate-loser files to Archive/Duplicates/
  4. Rename folders that I approved
  5. Remove empty folders that I approved
  6. Skip everything else

As you execute, post brief progress updates ("Archived 14 files from
Q3-Launch-2020 -> Archive/PM-Role-2021-2023/2020/"). If any action
fails, stop and ask me how to proceed via multiple choice.

## Phase 6 - Deliverables

When execution is complete, ask:
    "Cleanup is done. Which deliverables do you want?"
      A) All three (recommended)
      B) Summary report only
      C) Summary + proposed folder structure
      D) Just the follow-up list

Then produce the selected items and save them to my OneDrive under a
folder called "OneDrive-Cleanup-[YYYY-MM-DD]":

1. SUMMARY REPORT (Word document):
     - The cleanup scope used
     - The full Decision Log (every numbered question and answer)
     - Total files reviewed, kept, archived (by category), transferred,
       flagged
     - Folders renamed and empty folders removed
     - Any actions that failed during execution and why

2. PROPOSED FOLDER STRUCTURE for my current role:
     - A clean, role-relevant folder hierarchy for my active work
     - Based on my current role, current projects, and recent
       collaborators
     - Include a short rationale for each top-level folder

3. FOLLOW-UP LIST:
     - Files/folders that need a human decision I couldn't make
     - Suggested next step for each item
     - Any drafted handoff messages from transfer candidates

# Tone and pacing

- Talk to me like a colleague helping me clean my desk. Briefly explain
  your reasoning before each multiple-choice question.
- Move at a pace I can keep up with. If a folder is large, break it
  into smaller batches and pause between them.
- If I pick "Skip this folder" or "Leave it alone", remember and don't
  bring it up again in this session.
- If I want to stop early during planning, ask:
      "Want to pause planning here?"
        A) Yes, save the Decision Log so far and stop
        B) Just one more folder, then stop
        C) Keep going
  If I stop, save the partial Decision Log to OneDrive so I can resume
  later.

Begin with the hard-rules confirmation question.
```

---

## Customization Tips

Before sharing, the only field worth tweaking is the **age threshold** (currently "more than 3 years"). Suggested adjustments:

- **Less than 2 years tenure:** lower to 1 year
- **2 to 5 years tenure:** keep at 3 years
- **5+ years tenure with multiple roles:** keep at 3 years. The role-map step (Phase 1) will catch older items by role, not just by age.

Everything else (archive structure, hard rules, scope selection, multiple-choice interaction style, plan-then-execute flow) should work as-is across roles and teams.

## When to Use Which Scope

- **Entire OneDrive (Option A):** First-time cleanup, or annual full sweep. Plan for 60 to 90 minutes.
- **One specific folder (Option B):** Targeting a known problem area (an old project folder, a "downloads" graveyard, an archive that grew unwieldy). 15 to 30 minutes.
- **Multiple specific folders (Option C):** Tackling a related set (e.g., all folders from a former role) without committing to the whole drive. 30 to 60 minutes depending on volume.
