# Practice Rules

How this repo is used for Brian's Interview Prep track (system design, with behavioral interleaved).
The morning ritual in control-center reads this repo's commits through the public GitHub API.
**Commits are the only tracking**: no check-ins.

The full plan (every unit, its links, and its "done when" check) lives in control-center:
`/mnt/c/Users/brian/IdeaProjects/control-center/tracks/interview-prep.md` (Plan section).
The current unit is shown each morning on the dashboard's Interview Prep "Start Here" panel.

## Commit convention

End **every** session with at least one tagged commit, then push:

```
git add -A && git commit -m "[SD-10] Bitly redo, 42 min" && git push
```

Unit started but not finished:

```
git add -A && git commit -m "[SD-10 wip] got through high-level design" && git push
```

- The message must **start** with the unit ID in brackets: `[S-01]`, `[SD-01]` to `[SD-46]`,
  `[BH-01]` to `[BH-10]`, then `[SD-R01]`, `[SD-R02]`, ... for Continuous Reps.
- Add ` wip` inside the brackets when the unit is not finished. Only the commit **without** `wip`
  marks it complete.
- Untagged commits are ignored (no activity, no progress).
- Always use `git add -A` (new files are the normal case here; `git commit -am` would skip them).
- No catch-up: units are a sequence, not a calendar. A missed day is never made up and never counts
  as "behind".
- Everything is on `main`. No branches needed.

## What goes where

| Path | What | Written in |
|---|---|---|
| `system-design/framework.md` | Your one-page delivery framework, from memory, updated as you learn | SD-01, SD-02, then ongoing |
| `system-design/concepts.md` | Building-block notes (Monis, Hello Interview core concepts, Frank Kane gap-fills) | SD-03 to SD-06 |
| `system-design/technologies.md` | Key technology notes (Redis, Kafka, PostgreSQL, ...) | SD-07, SD-08 |
| `system-design/patterns/<pattern>.md` | 5 to 10 bullets per pattern | Pattern units |
| `system-design/<problem>/notes.md` | Study notes for a breakdown | Study units |
| `system-design/<problem>/redo.md` + diagram | Your timed redo (see template below) | Redo units |
| `system-design/mocks/<yyyy-mm-dd>-<problem>.md` | Mock, guided practice, and readiness-check summaries | Phase 3 and reps |
| `behavioral/log.md` | **One line per behavioral unit, nothing more** | BH units |

## Unit types

- **Study** (about 60 min): read the Hello Interview breakdown (and its video walkthrough if it has
  one), then write `notes.md`: key requirements, the deep dives, what surprised you.
- **Redo** (about 60 min): close the breakdown. Start a **45-minute timer**. Talk out loud while
  writing `redo.md` and drawing the diagram, framework order, requirements first. Then open the
  breakdown, fill in "What I missed", and commit.
- **Pattern** (about 45 to 60 min): read the pattern page, write 5 to 10 bullets.
- **Claude mock** (about 60 min): open a new Claude chat and paste:
  > Run a 45-minute system design mock interview: <problem>. Meta E5 calibration. Make me drive
  > with the delivery framework, push back like a real interviewer, then grade each framework step
  > strictly.

  Save a summary to `system-design/mocks/`.
- **Behavioral** (about 45 to 60 min): do the work in Hello Interview's Story Builder or behavioral
  pages, then add one line to `behavioral/log.md`.

## Redo template (`redo.md`)

```
# <Problem> redo, <yyyy-mm-dd>, <minutes> min

## 1. Requirements (~5 min)
Functional (3-5):
Non-functional (scale, latency, consistency vs. availability):

## 2. Core entities (~2 min)

## 3. API (~5 min)

## 4. High-level design (~10-15 min)
(diagram: <problem>.excalidraw or .png)

## 5. Deep dives (~10 min)

## What I missed vs. the breakdown

## One thing to do differently next time
```

## Confidentiality (this repo is public)

Safe: everything about public problems from public material, your framework and concept notes,
general engineering knowledge.

Keep out:
- **Story text.** Behavioral log lines only, for example
  `BH-03: Scope and Ownership stories drafted in Story Builder; source atoms: <atom IDs>`.
  Story facts stay in experience-vault; drafted delivery stays in Story Builder.
- **Atom IDs that contain internal names.** If an ID includes a codename, describe it generically instead.
- **Former-employer internals in system design notes.** Comparing in general terms is fine
  ("like a security pipeline I built"); naming internal systems, codenames, customers, or
  non-public numbers is not.

Quick test before any commit: would you be comfortable if a former employer's legal team read it?
