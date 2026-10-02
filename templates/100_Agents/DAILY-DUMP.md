# DAILY-DUMP.md — Inbox Sweep Engine

Turns raw daily-note captures into filed, linked notes. Runs nightly as a scheduled job (see `SCHEDULES.md`) or when the user says "run the sweep."

## The Idea

**One entrance.** Everything the user captures goes into `00_Daily_Notes/Inbox/YYYY-MM-DD.md`. The user captures; the sweep files. **If the user is deciding where a note lives, the system has failed.**

## Mode Gate

Read `MODES.md`, state the mode, then process **only items this mode owns**. Leave everything else on the note, untouched.

## Drain the Note

**Remove each item from the daily note the moment it is filed. When nothing is left, archive the note.** The note's contents are the status. This makes the sweep safe to re-run and safe for two instances to run in either order.

> [!DANGER] Removal goes last, every time
> **Write to the destination → read it back → then remove from the daily note.** If a write can't be verified, leave the item and say so. An undrained note is a visible problem; a lost capture is an invisible one.

**The daily note is not a task list.** Nothing carries forward to tomorrow. Every to-do routes to a tracker on the sweep that finds it.

## The Ownership Test

Only create a task when **the user clearly owns the next action**:

| Create a task | Don't |
| :--- | :--- |
| The user said they would do it | Someone else promised the user something |
| Their manager assigned it | The user is waiting on someone |
| They're named as owner | |
| They owe a reply or decision | |

**Unsure means drop it.** No task, no question. Leave it as context in the relevant note.

## Steps

### 0. Calendar look-back

Pull events since the last processed note. For every **key** meeting (the user runs it or presents), make sure a meeting note exists in `20_Areas/*/Meetings/`. If it's missing, create a stub flagged *No notes captured*. **Never reconstruct a meeting from memory. An invented meeting is worse than a missing one.**

### 1. People

Create or update a `30_People/` note for every person mentioned. **Initials, first name only, or a possible collision: don't create the note.** Add a confirmation item instead.

### 2. Companies

Create a `40_Companies/` note for every new company. Hand research to the specialist who owns companies, if you have one.

### 3. Route

| Content | Destination |
| :--- | :--- |
| Meeting notes | `20_Areas/<domain>/Meetings/YYYY-MM/` |
| Reference material | `50_Resources/<category>/` |
| Project context | The project note in `10_Projects/<domain>/` |
| A to-do the user owns (work) | A `- [ ]` line in the project's **Current State**. No project yet? Create a small one with `status: backlog` |
| A to-do the user owns (personal) | [Your personal tracker] |
| A task tied to a person | That person's **Action Items** |

Link everything (see Linking below).

### 4. Archive

When nothing is left to process, move the note to `60_Archive/YYYY-MM/`. **Never delete a daily note;** other notes link to it.

### 5. Memory

Update `MEMORY.md` within its size rules, and rewrite its **Sweep Status** block. Read immediately before writing.

### 6. Tomorrow's note

Create tomorrow's note from `90_Templates/Daily_Note.md` if it doesn't exist. Fill **Meetings** from the calendar and link the latest weekly reports. **Visibility only: no prep tasks, no reminders.**

## Linking

No person, company, project, or meeting stays plain text. Link **both directions**:

- **People ↔ Meetings:** attendee link on the meeting, an Interaction Log row on the person
- **People ↔ Companies:** set the person's `company` field
- **People ↔ Projects:** stakeholder links on the project, and back

**Check the person note, not just the meeting note.** A backlink resolving is not the same as the link being complete.

## Output

End with a short summary: mode, items filed, notes archived, notes left in the Inbox and why. Log it in `101_long_term_memory/`.
