# AI Brain

> **A starter vault that gives an AI assistant memory, a personality, a team, and a routine.**

Clone the repo, copy [`templates/`](templates/) into an Obsidian vault, connect an AI client with local file access, and make it yours. Every file is plain Markdown with `[placeholders]` to fill in or delete. See **Getting Started** below.

Inspired by Jason Cyr's [ai-agent-workflow](https://github.com/Jason-Cyr/ai-agent-workflow).

---

## The Idea

- **One entrance.** You capture everything into today's daily note. You don't file anything.
- **The assistant files it.** A nightly sweep moves each item to its home, links people and companies, and archives the note once it's empty.
- **The files are the memory.** The assistant starts every session with nothing. Its soul, its memory, and your profile are what make it the same assistant tomorrow.
- **It reports back.** Weekly reports show what you delivered, what you're carrying, and how life outside work is going.

---

## Getting Started

1. Install [Obsidian](https://obsidian.md) and create a vault locally.
2. Decide and connect your AI model (Claude or ChatGPT — highly recommended).
3. Clone this repo and copy everything in [`templates/`](templates/) into the root of your Obsidian vault.
4. Give your agent access to the vault on your machine, then say: *"Read AGENTS.md and start the session."*

Rename `AGENTS.md` if your client expects a different boot file (`CLAUDE.md`, `GEMINI.md`, and so on). MCP connectors for calendar, email, and chat are optional. **Keep secrets out** — anything in the vault can end up in the model's context.

---

## How It Flows

```
                                YOU
                                 │
                  type, dictate, paste, screenshot
                                 │
                                 ▼
               ┌───────────────────────────────────┐
               │  00_Daily_Notes/Inbox/            │  ← the only entrance,
               │  YYYY-MM-DD.md                    │    and the hand-off
               └─────────────────┬─────────────────┘    between modes
                                 │
        ┌────────────────────────┴────────────────────────┐
        ▼                                                 ▼
  WORK MODE                                         PERSONAL MODE
  Calendar · Email · Drive · Chat                   Calendar · Email · Drive · Chat
  on work accounts, + work wiki                     on personal accounts, + tracker
  e.g. Google Workspace, Slack, Notion              e.g. Gmail, Calendar, Linear
        │                                                 │
  files My Work items only                          files personal items only
        │                                                 │
        ▼                                                 ▼
  Project notes                                     Personal tracker, or
  10_Projects/11_My_Work/                           10_Projects/12_Personal/
        │                                                 │
        └────────────────────────┬────────────────────────┘
                                 ▼
          THE VAULT  ← the only surface the two modes share
      30_People/ · 40_Companies/ · 10_Projects/ · 20_Areas/
      50_Resources/ · 100_Agents/ (soul, memory, team, logs)
                                 │
       ┌─────────────────────────┼─────────────────────────┐
       ▼                         ▼                         ▼
  IMPACT.md (Fri)          STATUS.md (on demand)     LIFE.md (Sun)
  work mode                work mode                 personal mode
       │                         │                         │
       ▼                         ▼                         ▼
  21_My_Work/              11_My_Work/               22_Personal/
  Weekly_Summaries/        Status_Reports/           Weekly_Summaries/

               swept daily note → 60_Archive/YYYY-MM/
```

**The modes never talk to each other.** Each one files only what it owns and leaves the rest on the daily note. The note archives itself once both modes have swept it, so a note still sitting in the Inbox means something hasn't been filed yet.

| Connected app | Example | What the assistant does with it |
| :--- | :--- | :--- |
| Calendar | Google Calendar, Outlook | Finds meetings that need notes; fills tomorrow's agenda |
| Email | Gmail, Outlook | Summarizes threads; drafts replies (never sends without asking) |
| Drive / docs | Google Drive, OneDrive | Reads source docs and summarizes them into the vault |
| Chat | Slack, Teams | Pulls context from threads; drafts messages |
| Work wiki | Notion, Confluence | A work-only source to read from; also signals work mode |
| Task tracker | Linear, Todoist | Personal to-dos; also signals personal mode |

All of them are optional, and the vault stays the record. Other tools are sources to read from, not places to store knowledge.

---

## Folder Structure

```
templates/
├── AGENTS.md              ← Boot file. Loaded every session
├── 00_Daily_Notes/Inbox/  ← The only entrance
├── 10_Projects/           ← Has a finish line. Also the work task tracker
├── 20_Areas/              ← Ongoing responsibilities, meetings, weekly reports
├── 30_People/             ← One note per person
├── 40_Companies/          ← One note per company
├── 50_Resources/          ← Durable reference
├── 60_Archive/            ← Swept daily notes, by month
├── 90_Templates/          ← Note templates
└── 100_Agents/            ← The assistant, its team, and its processes
```

Projects and Areas split into `My Work` and `Personal`. Rename them to fit your life.

---

## The Assistant and Its Team

| File | What it gives the assistant |
| :--- | :--- |
| `SOUL.md` | Who it is: name, principles, tone, workflow |
| `USER.md` | Who you are and how you work |
| `MEMORY.md` | A short summary of what it has learned, with size rules so it stays short |
| `TEAM.md` | The specialists it can delegate to, and who owns what |
| `101_long_term_memory/` | Its dated session logs |

**The assistant is the orchestrator.** Specialists (a researcher, a writer, a red-team reviewer, whatever you need) each get their own folder in `102_Team/` with **their own soul, memory, and logs**, so each one keeps its own voice and knowledge between sessions. They report to the assistant, never straight to you. Copy `201_Example_Agent/` to add one.

---

## Modes

A mode is a **separate assistant instance with its own connected tools**. For example, one instance has your work accounts and another has your personal ones. They share only the vault.

You state the mode when a session starts. If you don't, the assistant works it out from which tools it can see, and it asks you when the signal is unclear. Each mode only changes what it owns. See `MODES.md`. If you only run one assistant, delete what you don't need.

---

## Inbox and Scheduled Jobs

| Job | When | Engine |
| :--- | :--- | :--- |
| Inbox sweep | Nightly | `DAILY-DUMP.md` |
| Impact report | Friday | `IMPACT.md` |
| Life report | Sunday | `LIFE.md` |
| Status report | On demand | `STATUS.md` |
| Memory prune | Monthly | `SCHEDULES.md` |

Each job is a single prompt. Set them up in your client's scheduler. See `SCHEDULES.md`.

---

## Reports

| Report | Answers | Shareable |
| :--- | :--- | :--- |
| **Impact** | What did I deliver, and what was it worth? | Part 1 |
| **Status** | What am I carrying right now? | Part 1 |
| **Life** | What's happening outside work? | No |

The three reports cover different ground and never repeat each other's content. Part 2 of each work report is a blunt read on your week, written for you only.

---

## License

[TBD]
