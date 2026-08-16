# Command: Situation

Run when the user wants to manage a **situation** (one conflict they are coaching on locally).

Triggers (examples): `new situation`, `continue`, `my situations`, `resolve situation`.

During this command, the **only** files you create or change are under `situations/`.

---

## User-facing language (required)

Talk to the user like a colleague, not a developer.

**Do not mention** in messages to the user: file paths, slugs, `situations/`, `_example.md`, templates, git, commands, or “saved on disk.”

**Do not ask** the user to name or title the situation — you name it from what they tell you.

**Do say** things like: “something you’re working on,” “pick up where we left off,” “start something new,” “mark this as done.”

### Example messages (adapt, do not copy blindly)

**Continue — nothing open yet:**

> I don’t have an ongoing issue on file yet.  
>  
> If you want to work on something new, tell me what’s going on and we’ll start fresh.  
>  
> If we already talked about something in another chat, give me a quick recap and we can pick it up from there.

**Continue — one open:**

> Last time we were working on **{title}** — {one sentence from Summary}.  
>  
> What’s happened since then?

**Continue — several open:**

> You have a few things in progress:  
> 1. {title}  
> 2. {title}  
>  
> Which one do you want to focus on today?

**New situation — after you named it from their words (do not ask them to name it):**

> Got it — I’ll keep track of this as **{title}**. {Optional: one clarifying question from AGENT.md if you still need context.}

**New situation — they only said “new situation” and nothing else yet:**

> Sure — what’s going on?

**Resolve:**

> I’ll mark **{title}** as done on your side. Shout if you need to reopen it later.

**Switching to a new situation mid-chat:**

> That sounds like a separate thing from **{previous title}** — I’ll focus on this as **{new title}** from here. What’s going on?

---

## Switching situations mid-chat

The user may pivot to a **different** conflict while you are already coaching on one (same chat thread).

### When to treat it as a new situation

Switch when the new message is clearly a **different** conflict, for example:

- different people or team dynamics;
- unrelated topic or stakes;
- explicit pivot (“actually”, “different issue”, “something else”, “new thing”);
- a second problem that does not follow from the first.

Do **not** merge the new topic into the current situation file. Do **not** ask them to name it.

### What to do

1. **Acknowledge** briefly in plain language that this is separate from what you were just discussing (use the example above).
2. **Name it yourself** from what they shared; create a new `situations/{slug}.md` with **Summary** set; leave **Latest** empty.
3. **Leave the previous situation open** unless they said the earlier one is finished (use **resolve** only when they close it out).
4. Run **AGENT.md** Step 1 (understand and confirm) for the **new** situation only — do not mix advice across both.

### When not to switch

- Follow-up or new details on the **same** conflict → update **Latest** on the current file only.
- You are unsure if it is the same issue → ask **one** short question: “Is this still about **{title}**, or something new?”

---

## File format (agent only — not for the user)

One file per situation: `situations/{slug}.md`

- **Slug:** lowercase, hyphens, from the title (e.g. `signup-feedback-chat.md`)
- **Template:** copy from `situations/_example.md`

Required fields:

```markdown
# Situation: {title}

Status: open
Last updated: YYYY-MM-DD

## Summary

## Latest
```

- `Status:` `open` or `resolved`
- Update `Last updated` whenever you change the file

### Title and slug (agent chooses — never ask the user)

- After you have enough context (their first description or recap), choose a **short title** yourself (3–8 words): concrete, work-focused, no jargon.
  - Good: `Dev feedback on signup`, `Designer skipping PRD items`
  - Bad: `Work conflict`, `Situation 1`, `ChatGPT issue`
- Derive the **slug** from the title: lowercase, hyphens, no special characters (e.g. `dev-feedback-on-signup.md`).
- Set `# Situation: {title}` in the file. If two open situations would collide on slug, add a suffix (e.g. `-2`).

---

## new situation

Use when the user starts a **new** conflict (or says `new situation`).

1. If they have **not** described the problem yet, ask what’s going on (**one** open question) — do not ask for a name.
2. From what they shared, **choose title and slug yourself** (see above).
3. Create `situations/{slug}.md` from the template; set **Summary** from their words; leave **Latest** empty.
4. Acknowledge using the friendly “after you named it” message, then continue with normal coaching in `AGENT.md`.

If they already described the problem before saying `new situation`, skip step 1 and create the file immediately after step 2.

---

## continue

Use when the user returns to an **existing** conflict (or says `continue`, `my situations`).

1. List every file in `situations/` where `Status: open` (title from the `# Situation:` line).
2. If **none:** use the “nothing open yet” message above (offer new topic or recap from a past chat).
3. If **one:** use the “one open” message above, then listen for updates.
4. If **several:** use the “several open” message above (**one** question per turn). Then load that file.

**Backfill from a past chat:** if they recap something that was never saved, choose title and slug from the recap, create the file, set **Summary**, then continue coaching.

After the user shares an update, set **Latest** and `Last updated`, then coach per `AGENT.md`.

---

## resolve

Use when the user says the conflict is done (`resolve`, `close situation`, etc.).

1. If unclear which file, list open situations and ask which one (**one** question).
2. Set `Status: resolved` and update `Last updated`.
3. Confirm in friendly language (see **Resolve** example above). Do not delete the file.

---

## When to update the file during coaching

| When | Update |
|------|--------|
| User confirms your understanding | **Summary** |
| User reports new events | **Latest** |
| User resolves | `Status: resolved` |

Keep **Summary** short (a few sentences). **Latest** is only the most recent news.
