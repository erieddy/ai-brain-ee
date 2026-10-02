# MODES.md — Operating Modes

A mode is **a separate assistant instance with its own connected tools**, not a setting. Each instance sees its own accounts. **The vault is the only thing they share.**

## Which Mode You're In

**The user states the mode at session start. Take it as authoritative.**

**Failsafe:** discover it from the tools this instance can see. Pick a signal that exists in exactly one instance.

| Signal | Mode |
| :--- | :--- |
| [Work-only tool, e.g., your work wiki] is connected | `work` |
| [Personal-only tool, e.g., your personal task tracker] is connected | `personal` |
| Both, or neither | **Ask. Do not guess** |

Tools connected in both instances (calendar, email, chat) are never the signal.

**State the mode, stated or detected, in your first response.** There is no stored mode field; a stored value goes stale. If a document disagrees with what is connected, the connectors win.

## `work`

- **Scope:** My Work: projects, meetings, colleagues, customers, career
- **Connectors:** [List]
- **Task tracker:** project notes in `10_Projects/11_My_Work/`
- **Reports:** Impact (weekly), Status (on demand)

## `personal`

- **Scope:** Family, home, health, finances, side projects
- **Connectors:** [List]
- **Task tracker:** [Your personal tracker, or project notes in `10_Projects/12_Personal/`]
- **Reports:** Life (weekly)

## Rules

1. **Reading is not gated.** Every instance can read the whole vault
2. **Writing is gated.** Only change items your mode owns
3. **Leave what you don't own untouched.** No moving, reformatting, or summarizing it
4. **A tool missing from this instance is out of scope, not broken.** Never report it as a defect
5. **The vault is the bridge.** A fact crosses domains by being written into the vault by one instance and read by the other
6. **Two instances, one set of files, no locking.** Read immediately before writing, and append rather than replace

## Running a Single Mode

Only one assistant? Delete this file's second section, keep the rules about scope, and remove step 4 from `AGENTS.md`.
