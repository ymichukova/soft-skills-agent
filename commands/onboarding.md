# Command: Onboarding

Run this command when:
- the user is new and has no profile yet;
- `user_profile.md` is missing or incomplete;
- the user asks to set up or update their profile (e.g. "onboarding", "update my profile").

Do **not** give conflict advice until onboarding is complete or the user explicitly skips.

During onboarding, the **only** file you create or change is `user_profile.md`. Do not create other files or store answers elsewhere.

---

## Critical rules

### One question per turn

**Never** post all onboarding questions in a single message.

Each turn while collecting answers:
1. Ask **exactly one** question (intro may include Question 1 only).
2. Wait for the user's answer.
3. **Remember the answer in the conversation** — do not write to disk yet.
4. Ask the next question (or finish and write the file).

### When to write `user_profile.md`

| Flow | When to write |
|------|----------------|
| **Full onboarding** (all four questions) | Only after Question 4 is answered — write the complete profile in one step. |
| **Partial update** (one field) | Immediately after that single answer — update only that field. |
| **Interrupted** (stopped before Q4) | Do **not** write a partial file. |

If the user stops mid-flow and returns in the **same chat**, continue from the next unanswered question. In a **new chat** without a complete profile, start from Question 1.

---

## Step 1 — Intro

If onboarding is just starting, send a short intro. You may include **Question 1** in the same message.

Example:

> Before we work on situations, I want to understand how you communicate at work. You can run **onboarding** again anytime to update this.
>
> Then ask Question 1 (see below).

---

## Step 2 — Question sequence (strict order)

Ask questions **in this order**. For a full re-onboarding, ask all four even if `user_profile.md` already exists (overwrite with new answers at the end).

| Step | Field | Question |
|------|-------|----------|
| 1 | `Preferred tone` | Question 1 |
| 2 | `Confrontation comfort` | Question 2 |
| 3 | `Seniority` | Question 3 |
| 4 | `Environment` | Question 4 |

### Question 1 — Preferred tone

> **What tone feels most natural for you in difficult conversations?**
>
> 1. Gentle — warm, careful wording  
> 2. Balanced — clear but not harsh  
> 3. Direct — concise, minimal softening

### Question 2 — Confrontation comfort

> **How comfortable are you with confrontation at work?**
>
> 1. Low — I usually avoid conflict  
> 2. Medium — depends on the situation  
> 3. High — I'm comfortable pushing back directly

### Question 3 — Seniority

> **What best describes your seniority?**
>
> 1. Junior PM  
> 2. Mid-level PM  
> 3. Senior PM / Lead

### Question 4 — Work environment

> **What kind of environment do you work in?** (Short answer is enough — e.g. startup, enterprise, remote team, highly political org.)

Map numbers (1/2/3) to the corresponding option. If ambiguous, ask one short clarifying question — still only one question in that message.

---

## Step 3 — Write `user_profile.md`

After all required answers are collected:

1. Read `user_profile.md` if it exists (to preserve any extra sections the user added manually).
2. **Create** or **update** the file with all four answers at once (full onboarding) or only the changed field (partial update).
3. Set `Last updated` to today's date (YYYY-MM-DD).
4. Set `Onboarding completed` to `yes` (full onboarding only).

Use this structure:

```markdown
# User Profile

Last updated: YYYY-MM-DD
Onboarding completed: yes

## Communication preferences

- **Preferred tone:** {Gentle | Balanced | Direct}
- **Confrontation comfort:** {Low | Medium | High}

## Work context

- **Seniority:** {Junior PM | Mid-level PM | Senior PM / Lead}
- **Environment:** {user's short answer}
```

Normalize answers:
- Tone → Gentle | Balanced | Direct
- Confrontation comfort → Low | Medium | High
- Seniority → Junior PM | Mid-level PM | Senior PM / Lead
- Environment → user's short free-text answer

---

## Step 4 — Finish

After writing `user_profile.md`:

1. Send **one** short summary of what you saved (bullet list).
2. Tell the user they can say **onboarding** anytime to update.
3. Invite them to describe their situation (main `AGENT.md` flow).

Do not ask another onboarding question after this.

---

## Other rules

- If the user refuses onboarding, note it in chat and continue with neutral defaults.
- Do not store sensitive personal data (colleague names, legal details, etc.) in `user_profile.md`.
