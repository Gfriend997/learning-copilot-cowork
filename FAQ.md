# FAQ

Common questions about using Cowork. New entries get added as the same questions come up.

## How do I schedule a task to run on a recurring basis?

Tune the prompt first. Once you have output you like, append a scheduling instruction at the end.

**The workflow:**

1. Run the prompt manually a few times. Adjust until the output is reliable.
2. At the end of the working prompt, add a scheduling line: *"Schedule this to run [frequency] at [time]. Skip [holidays / PTO / days my calendar is blocked]."*
3. Cowork creates a scheduled-prompt entry. **It is created in a draft state, not active.**
4. Activate the draft so it actually runs. Cowork asks: **Activate and run now** (fires immediately so you can watch and approve actions) or **Activate** (first run at the next scheduled time). Until you pick one, nothing fires.

**Example daily-briefing prompt:**

```
Pull my meetings, sent emails, and outstanding tasks from yesterday and today.
Tell me what I need to focus on. Be opinionated about priorities; do not
just list things.

Schedule this to run every weekday at 8 AM and again at 4 PM. Skip company
holidays and any day my calendar shows blocked PTO.
```

**Limits and management:**

- No published limit on the number of scheduled prompts per user as of this writing. If you find one in practice, open an issue.
- Manage schedules from the **Scheduled** tab in the Tasks view, or the **Schedule** section of the side panel.
- For each schedule you can edit, pause, resume, or delete.

**Common reason a scheduled prompt is not firing:** you forgot to activate it after creating it. The draft state is silent. Check the Scheduled tab and confirm the entry shows as active.

**A worked example:** [`Prompts/OneDrive_Maintenance_Schedule_Prompt.md`](Prompts/OneDrive_Maintenance_Schedule_Prompt.md) is this whole pattern applied to OneDrive upkeep. It runs once with your approval, then keeps the drive tidy on a schedule using inline (remembers) memory mode. Good reference for how a real recurring task is structured.

---

*More questions land here as they come up. If something you ran into is missing, open an issue.*
