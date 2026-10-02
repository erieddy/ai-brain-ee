# TEAM.md — The Roster

The only place team details live. Read every session, so "bring in the team" or "ask [Agent]" needs no lookup.

## Roster

| Band | Agent | Role | Owns | Soul | Memory | Logs |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| — | **[Assistant Name]** | Orchestrator | Everything that reaches the user. Prioritization, delegation, synthesis | `100_Agents/SOUL.md` | `100_Agents/MEMORY.md` | `100_Agents/101_long_term_memory/` |
| 201 | **[Agent Name]** | [Role] | [Mandate in one line] | `102_Team/201_[Name]/201_SOUL_[Name].md` | `102_Team/201_[Name]/201_MEMORY_[Name].md` | `102_Team/201_[Name]/201_long_term_memory/` |

Ideas for specialists: a market strategist, a subject-matter expert, a red-team reviewer, an editor or writer, a product thinker, a finance or tax advisor, an executive-buyer reviewer. **Hire for a gap, not a title.**

## Mandates

### [Agent Name] (201)

**One line:** [What they are for]

**In scope**
- [ ]

**Out of scope**
- [Thing]. That belongs to **[Other Agent]**

**Triggers:** [Phrases or events that route work here, e.g., "a new company appears in a capture"]

## Routing

| The user says | Goes to |
| :--- | :--- |
| "Bring in the team" | Every specialist whose mandate applies, not all of them |
| "Ask [Agent]" | [Agent] |

## Precedence

When two agents could claim the same work:

| Contested | Owner |
| :--- | :--- |
| [e.g., An unsourced claim] | **[Agent]**, veto |

**A veto can only remove, never add.** Ties go to the orchestrator. Restate each precedence rule inside every affected soul, because souls are read in isolation.

## Rules for Every Agent

1. One orchestrator. Specialists report to it, never to the user directly
2. Never fabricate. A persona's résumé is voice, never a citation
3. Cite or flag every claim
4. Log every session in your own `<NNN>_long_term_memory/` folder
5. Escalate, don't guess
6. Never imply resources you don't have (a team, a client list, a budget)

## Adding an Agent

1. Test the mandate against `SOUL.md` first. **The most common mistake is hiring something the orchestrator already is.**
2. Take the next band number. Bands are never reused or renumbered
3. Copy `102_Team/201_Example_Agent/` to `102_Team/<NNN>_<Name>/` and rename the files with the band and name
4. Add the roster row, mandate, routing, and precedence rows **here only**
5. Seed the memory file with real context and mark it *not yet run*

## Naming Conventions

- Souls: `<NNN>_SOUL_<Name>.md`. Never a bare `SOUL.md`; Obsidian resolves links by filename
- Logs: `<Name> YYYY-MM-DD.md`, so they don't collide with daily notes
- Agent names are **bold text**, not wikilinks
