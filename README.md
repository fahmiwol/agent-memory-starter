# Agent Memory Starter

**Your AI agent is brilliant inside one conversation and amnesiac between them.**

So you re-paste the same context every morning. You get advice that contradicts a decision you
made last week. You watch it confidently suggest an approach you already tried and abandoned in
March, with no memory that it failed.

That is not a model weakness. It is a missing storage layer *outside* the model — and you can
build it today with four Markdown files and a ritual.

This repository is the whole starter system. Everything is below; you do not need to download
anything to use it.

---

## The idea in one table

Split memory into four types, because the agent needs to know which one to reach for.

| Type | Contains | Behaviour |
|---|---|---|
| **People** | how you work, your language, your pet peeves | rarely changes, read every session |
| **Decisions** | what is settled and must not be reopened | accumulates |
| **Failures** | what was tried and did not work | accumulates, **most often skipped** |
| **State** | current status | safe to overwrite |

The third is the expensive one to skip. Without failure notes your agent will suggest the same
dead end three months from now, with exactly the same confidence.

---

## The three prompts

These three are the minimum ritual: open, record on failure, close.

### 1. Opening a session

Paste this first, before asking for anything.

> Read `memory/INDEX.md`. State: (a) what is being worked on, (b) which decisions bind this task,
> (c) which failures are already recorded in this area. Do not propose anything until you have
> stated all three.

If the agent jumps straight to a solution without naming a single note, it skipped the step.
Make it start over.

### 2. Recording a failure, as it happens

Paste this the moment something does not work. Do not save it for the end of the session —
by then you only remember what worked.

> This failed: [what failed]. Write a failure note: what was tried, what happened, suspected
> cause, and what rule this produces. Do not soften it.

The "what rule this produces" part is what separates a useful note from a complaint.

### 3. Closing a session

Two minutes, and it decides whether the next session starts from zero.

> Write a handoff for the next session: current state, what was done today, the next concrete
> step, and the traps to avoid. Write it for a reader who was never in this session, so avoid
> "it" and "the thing from earlier".

---

## The note format

One idea per file. The frontmatter is what lets an agent judge relevance without reading
everything.

```markdown
---
name: change-this-filename
description: one sentence, used by the agent to judge relevance
type: decision
date: 2026-01-01
---

Write the content here. One idea only.

**Why:** the reasoning that led to this.

**When this may be reopened:** the condition that makes it expire.

Related: [[other-note]]
```

`**When this may be reopened**` is the line most people leave out, and it is the one that stops
your memory folder from becoming a graveyard of rules nobody dares delete.

---

## Start in twenty minutes

1. Create a `memory/` folder in your project.
2. Copy [`note-template.md`](note-template.md) into it and write down **one decision you made
   this week, including the reason**.
3. Open your next session with prompt 1.
4. Close it with prompt 3.

If after a week your agent starts referencing old decisions without you retyping them, the
method is working. If it does not, you have lost twenty minutes and four files.

---

## What is in this repository

| File | What it is |
|---|---|
| [`3-core-prompts.md`](3-core-prompts.md) | the three prompts above, with notes on when each fails |
| [`daily-session-checklist.md`](daily-session-checklist.md) | the open / work / close ritual, including the monthly audit |
| [`note-template.md`](note-template.md) | the note format with its four required sections |
| [`id/`](id/) | the complete Bahasa Indonesia edition |

Works with any agent that can read files in your project: Claude Code, Cursor, Windsurf, Codex,
Copilot, or a plain chat window you paste into. There is nothing to install and no vendor to
depend on.

---

## Honest limits

This is a **method**, not software. It has no code, no MCP server and no automation — you and
your agent maintain the files by hand. That is deliberate: a method survives you switching
tools, and plain Markdown is readable by every agent that exists.

If you want the same idea as an actual server your agent queries, that is a different tool —
see *Second Brain Kit* below.

---

## If this works for you

The full method, **Agent Memory OS**, adds the folder layout and index format, twelve prompts
covering the whole work cycle, a handoff template for crossing between sessions, and five real
bad-versus-good examples taken from mistakes that actually happened.
→ [Agent Memory OS — $5](https://fahmiwolf.gumroad.com/l/npfhry)

And if you would rather your agent *query* a memory instead of reading files:
→ [Second Brain Kit — one memory for every AI agent, over MCP, $7](https://fahmiwolf.gumroad.com/l/ezqudk)

Other tools from the same shop: [fahmiwolf.gumroad.com](https://fahmiwolf.gumroad.com)

---

## Licence

Use it for your own work, personal or commercial, on any number of projects. Modify it freely.
Do not resell it as your own product. See [LICENSE.md](LICENSE.md).
