# soft-skills-agent

PM Conflict Coach — an AI agent that helps product managers handle difficult workplace situations: conflicts with engineers, designers, stakeholders, or other PMs. You describe the situation, the coach helps you figure out what's going on and how to handle the conversation.

It runs locally in **Cursor** or **Claude Code** — no server, no install. The agent is a set of markdown files that your AI editor reads and follows.

---

## Get the agent

**Option A — clone (if you use git):**

```bash
git clone https://github.com/ymichukova/soft-skills-agent.git
```

**Option B — download:** on the repo page, click **Code → Download ZIP**, then unzip the folder somewhere convenient.

---

## Run it in Cursor

1. Open the folder in Cursor (**File → Open Folder**).
2. Open a new chat and attach `AGENT.md` (type `@AGENT.md`).
3. Say hi. On first run the coach will ask a few onboarding questions (tone, seniority, work context) and save your answers to `user_profile.md`.
4. Describe your situation.

Tip: keep one conflict per chat. Start each new chat by attaching `AGENT.md` again.

## Run it in Claude Code

1. In a terminal, go to the folder and start Claude Code:

```bash
cd soft-skills-agent
claude
```

2. Say hi. The project's `CLAUDE.md` points Claude at the coach automatically — it will run the same onboarding on first use, then coach you.

The Claude Code desktop app works the same way: open the folder as a project and start chatting.

---

## Using the coach

- **First session** — the coach runs a short onboarding and creates `user_profile.md`. This shapes how it talks to you (e.g. how direct it is).
- **Describe a conflict** — just tell it what's going on, in your own words. Or say **`new situation`** to have it tracked in a file.
- **Come back later** — in a new chat, say **`continue`** to pick up an open situation where you left off.
- **Wrap up** — say **`resolve situation`** when a conflict is settled.
- **Update your profile** — say **`onboarding`** anytime.

## Your data stays local

Everything personal — `user_profile.md` and anything under `situations/` — is written only to your local folder and is **gitignored**, so it can't be committed or pushed back to this repo. Delete those files anytime to start fresh.

---

## Concepts

### Profile

**Who you are** as a communicator — long-lived, one per user.

- File: `user_profile.md`
- Set via `commands/onboarding.md`
- Applies to every situation

### Situation

**One workplace conflict** you are working through with the coach.

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
