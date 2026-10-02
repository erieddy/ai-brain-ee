# SCHEDULES.md — Scheduled Jobs

Recurring jobs that keep the vault organized without being asked. Set them up with your client's scheduler (scheduled tasks, cron, a launch agent). Each job is just a prompt.

| Job | When | Mode | Prompt |
| :--- | :--- | :--- | :--- |
| `daily-sweep` | Nightly, [19:00] | each | "Run the inbox sweep in `100_Agents/DAILY-DUMP.md`." |
| `weekly-impact` | Friday, [16:00] | `work` | "Run the weekly impact report in `100_Agents/IMPACT.md`." |
| `weekly-life` | Sunday, [18:00] | `personal` | "Run the weekly life report in `100_Agents/LIFE.md`." |
| `memory-prune` | Monthly, [1st] | each | "Prune `100_Agents/MEMORY.md` and each team memory file to their size rules. Delete anything resolved." |

**On demand only:** the Status report (`STATUS.md`). It's a snapshot; schedule it if you want a regular one.

## Rules

- **Order matters.** Reports read what the sweep filed. Run the sweep before a report, or the report is built on gaps
- **Unattended jobs follow the same Ask First list** in `AGENTS.md`. They draft; they don't send
- **Every run logs** to `101_long_term_memory/`. Check the vault, not just the log: a log can claim work that didn't happen
- **Pick off-peak minutes** (e.g., 19:07, not 19:00) if your scheduler is shared
