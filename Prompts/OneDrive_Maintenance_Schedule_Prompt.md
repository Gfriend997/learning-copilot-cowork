# OneDrive Maintenance Schedule Prompt

A reusable Copilot Cowork prompt that organizes your OneDrive once, then **keeps it tidy on a schedule**. This is the maintenance layer that runs after the one-time deep clean ([`OneDrive_Cleanup_Prompt.md`](OneDrive_Cleanup_Prompt.md)).

Why it matters: a coherent file structure is not just tidiness. It measurably lifts Cowork's output quality. Cowork pulls context from your OneDrive every time it drafts, finds, or suggests. When the structure stays consistent over time, Cowork files related information together and reasons better. Let the drive drift and output quality drifts with it.

Safe by design: **nothing is ever deleted.** The first run pauses for your approval before any change. After that, it runs unattended on your schedule and emails you a full list of every file it moved.

---

## How It Works

- **First run is interactive.** Phases 1 and 2 pause for your approval. You confirm the folder taxonomy, naming convention, and protected folders before anything moves.
- **Scheduled runs are unattended.** They reuse the structure you approved, touch only files added or changed since the last run, and email you the results.
- **Inline memory mode is required.** The recurring task must remember your approved taxonomy across runs. A fresh-each-run task would forget it and re-interview you every time. See [FAQ: scheduling a recurring task](../FAQ.md).

## How to Use

1. Copy the prompt below (everything inside the code block).
2. Paste it into a new Copilot Cowork chat.
3. Walk through Phases 1 and 2. Approve the proposed structure, naming convention, and protected folders.
4. Approve Phase 3. Cowork organizes your loose files and emails the report.
5. In Phase 4, accept the offer to schedule it. Pick a quiet time and **inline (remembers) memory mode**.
6. Activate the scheduled draft so it actually fires. See the FAQ on activation.

---

## The Prompt

```
Help me organize my OneDrive so files are consistent and easy to find, then
keep it tidy on a schedule. Work in four phases and pause for my approval
before making any changes.

# Hard rules (apply in every phase and every run)

- NEVER delete anything. The only action on a file is to move or rename it.
- NEVER touch my Cowork folder (OneDrive/Documents/Cowork/). Leave it
  completely untouched. Add any other protected folders I name in Phase 1.
- NEVER move, rename, or touch files that are sensitivity-labeled
  (Confidential, Restricted, etc.), under legal hold, contain obvious PII or
  regulated data, or live in folders named for legal, HR, finance, or
  compliance. If unsure, treat as sensitive: leave it in place and note it.
- NEVER rename a file that is shared, has an active sharing link, or is
  already correctly filed. Renaming breaks links. Apply the naming
  convention only to loose files you are moving for the first time.
- SKIP any file currently open, locked, or actively syncing. Note it and
  pick it up on the next run.

PHASE 1 - Understand my work (no changes yet)

Look up my job title and role from my M365 profile.

Scan my recent emails, calendar events, and existing OneDrive folders to
infer the main categories of work I deal with (projects, recurring meetings,
teams I work with, document types, external vs. internal, etc.).

Then ask me 3 to 5 short questions to fill any gaps. For example: which
projects or clients are active, which folders are off-limits, and whether I
prefer organizing by project, by document type, or by date.

PHASE 2 - Propose a structure (no changes yet)

Present a proposed folder taxonomy (top-level categories plus key subfolders)
with a one-line rationale for each, based on what you found in Phase 1.

Propose a file-naming convention (default: YYYY-MM-DD_topic).

Show me a preview of where loose and unsorted files would move, and flag any
you cannot confidently place.

Wait for my approval or edits before doing anything. Once I approve, remember
the approved taxonomy, naming convention, and full protected-folder list for
all future runs.

PHASE 3 - Organize (after I approve)

Scan my OneDrive for loose files in the root and other unsorted locations,
plus anything added or modified since the last run, and move them into the
approved folders, creating folders as needed and renaming per the convention.

Act only on loose or newly-added/changed files. Do NOT re-move or re-rename
files that are already correctly filed.

Send suspected duplicates and files you cannot confidently place to a folder
named "_Review" at the root. Leave genuinely ambiguous files where they are
and note them instead of guessing.

PHASE 4 - Report and offer to schedule

Email me the results. Subject: "OneDrive Organization - <run date>". Body must
list every folder created and every file moved (original location, new
location, reason), plus anything left in place or routed to _Review and why.
If the _Review folder holds more than 15 items, say so at the top so I clean
it out manually. If nothing changed, still email a short "no changes" note.

Then ask whether I would like to turn this into a recurring task, and explain
these choices so I can decide well:

 - Cadence: daily suits high-volume folders; weekly suits lighter ones. Pick
   a quiet time (for example a weekday evening) so it runs when I am not
   working in the files.
 - Memory mode: use an "inline" recurring task that REMEMBERS across runs, not
   a "separate"/fresh-each-run one. Inline mode reuses the taxonomy I approved
   in Phase 2 and can tell what was added since the last run, so the structure
   stays consistent. A fresh-each-run task would forget the approved structure
   and re-interview me every time. Avoid that for this job.

# Behavior on scheduled re-runs

On scheduled re-runs, do NOT repeat Phase 1 or Phase 2 and do NOT re-interview
me. Reuse the taxonomy, naming convention, and protected-folder list I approved
on the first run. Go straight to Phase 3 (organize only files added or changed
since the last run) and Phase 4 (email the report).
```

---

## Customization Tips

- **Naming convention:** `YYYY-MM-DD_topic` is the default. If most of your files are project-driven rather than date-driven, change it to `Project_topic_YYYY-MM-DD` so the project sorts first.
- **_Review threshold:** the prompt flags _Review when it exceeds 15 items. Lower it to 5 if you want to stay on top of edge cases; raise it if you run a high-volume drive and only want a heads-up when it really piles up.
- **Cadence:** start daily for the first two weeks so you see it working, then drop to weekly once the structure is stable and the daily emails mostly say "no changes."
- **Protected folders:** name every off-limits folder in Phase 1. The Cowork folder is protected automatically. Add client folders under NDA, anything shared with a team, and any folder you manually curate.

## How This Differs From the One-Time Cleanup

| | [`OneDrive_Cleanup_Prompt.md`](OneDrive_Cleanup_Prompt.md) | This prompt |
|---|---|---|
| **Purpose** | One-time deep clean | Ongoing maintenance |
| **Interaction** | Multiple-choice, every move gated | First run gated, then unattended |
| **Scope** | Whole drive or chosen folders, past roles, duplicates, stale items | Loose and newly-added files only |
| **Runs** | Once, or annual sweep | Daily or weekly, on a schedule |
| **Output** | Summary report, proposed structure, follow-up list | Emailed change log per run |

Run the deep clean first to establish the structure. Then run this to keep it that way.
