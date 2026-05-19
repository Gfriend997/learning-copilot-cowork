# Step 1: Personalize Copilot

**Prompt:** [`_Prompts/Copilot_Personalization_Interview.md`](../_Prompts/Copilot_Personalization_Interview.md)

## Why First

Cowork inherits context from Microsoft 365 Copilot through Work IQ. If your Copilot profile is generic, every Cowork output will be generic. Fix the foundation before doing anything else.

## Checklist

- [ ] Sign in to Copilot at [m365.cloud.microsoft](https://m365.cloud.microsoft)
- [ ] Open Settings, go to **Personalizations**
- [ ] Turn on **Save memory** so Copilot accumulates context about you over time
- [ ] Open a fresh Copilot Cowork chat
- [ ] Upload `Copilot_Personalization_Interview.md` as an attachment, or paste its contents into the chat
- [ ] Ask Cowork to execute the prompt
- [ ] Choose **Full mode** (25-30 min, full depth) or **Express mode** (10 min, highest-leverage areas only). Express is the right starting point for most people.
- [ ] Answer the interview questions one at a time
- [ ] Copy the final output (around 5,000 characters) into Settings, Personalizations, **Custom Instructions**
- [ ] Run the three test prompts the interview suggests, to verify the instruction actually changed Cowork's behavior

## What the Interview Does

The Personalization Interview is more than a generic questionnaire. It:

- **Auto-loads your work profile** before asking anything (name, role, manager, reports, calendar types, file types). Every question after that is tailored to your actual role.
- **Skips irrelevant sections.** No "email to direct reports" questions if you do not manage anyone. No technical-spec questions if you are in marketing.
- **Tunes example options to your role.** A salesperson sees deal and renewal examples. An engineer sees design-review examples.
- **Enforces a Sounding Board section.** This is the anti-sycophancy guardrail. Without it, Copilot defaults to yes-person behavior. The prompt protects this section even when trimming for character count.
- **Manages the character budget.** Copilot's Custom Instructions field hard-caps at 8,000 characters. The prompt aims for 5,000 to leave you ~3,000 characters of headroom for future edits.

## Tips

- **Run it in a fresh Cowork chat.** Context from prior conversations can pollute the interview.
- **Express mode first.** Get something working. You can re-run Full later to deepen.
- **Answer with examples, not adjectives.** "Like the email I sent to Acme last Tuesday" beats "professional but warm."
- **Save the final instruction text somewhere editable** (a OneDrive note or a future Compass file). You will want to tune it after a week of real use.
- **Re-run quarterly.** Roles, audiences, and preferences drift. The interview takes 10 minutes in Express mode; the payoff lasts a quarter.

## What You Have After This Step

- A Custom Instructions string pasted into Copilot Personalizations (around 5,000 characters)
- A backup of that string saved somewhere you can edit
- Save Memory turned on
- Three verified test prompts confirming Cowork's behavior shifted

When that is true, move to [Step 2: Clean Your OneDrive](02-clean-onedrive.md).
