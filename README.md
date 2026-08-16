# soft-skills-agent

PM Conflict Coach — an agent that helps product managers handle difficult workplace situations. Run locally in Cursor: `AGENT.md` (coaching), `commands/onboarding.md` (profile), `commands/situation.md` (situations).

---

## Concepts

Use these terms consistently in docs and commands.

### Profile

**Who the user is** as a communicator — long-lived, one per user.

- File: `user_profile.md`
- Set via `commands/onboarding.md`
- Applies to every situation

### Situation

**One workplace conflict** the user is working through with the coach.

- Evolves over time (new events, follow-ups, revised advice)
- Can span many chat **sessions**
- File: `situations/{slug}.md` (local, gitignored — see `situations/_example.md`)
- Commands: `commands/situation.md` (`new situation`, `continue`, `resolve`)

### Session

**One chat thread** (e.g. one Cursor conversation).

- Many sessions can belong to one situation
- One session should focus on one situation at a time; use `continue` in a new chat to load it

### How they relate

```
Profile    →  all situations
Situation  →  one conflict (many sessions)
Session    →  one chat
```

### Naming

| Say | Mean |
|-----|------|
| “**New situation**” | A new conflict to coach |
| “**Continue**” | Load an open situation (`commands/situation.md`) |
| “Describe your **situation**” | User’s opening narrative (`AGENT.md`) |
