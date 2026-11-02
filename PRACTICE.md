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

All paths are relative to the repo root (`/mnt/c/Users/brian/IdeaProjects/interview-prep-practice`).
Most units create a new file. Git does not track empty folders, so before creating a file, run
`mkdir -p` for its folder (for example `mkdir -p system-design/bitly`).

| Path | What | Created in |
|---|---|---|
| `system-design/framework.md` | Your one-page delivery framework. Two headings: `## What E5 interviewers expect` (5 bullets) and `## Delivery framework` (the 5 steps with time boxes, from memory). Update it in the same commit whenever a redo or mock changes how you run the framework | SD-01 creates it, SD-02 fills the second heading |
| `system-design/concepts.md` | Building-block notes, one `##` heading per video or topic (Monis, Hello Interview core concepts, Frank Kane gap-fills) | SD-03, updated SD-04 to SD-06 |
| `system-design/technologies.md` | Key technology notes, one `##` heading per technology (Redis, Kafka, PostgreSQL, ...) | SD-07, updated SD-08 |
| `system-design/patterns/overview.md` | One line per common pattern, plus the Top 10 problems list | SD-08 |
| `system-design/patterns/<pattern>.md` | 5 to 10 bullets per pattern | Pattern units |
| `system-design/<problem>/notes.md` | Study notes for a breakdown | Study units |
| `system-design/<problem>/redo.md` | Your timed redo (see template below) | Redo units |
| `system-design/<problem>/<problem>.excalidraw` | The redo diagram: draw at https://excalidraw.com, then menu > Save to disk (a `.png` export is fine instead) | Redo units |
| `system-design/mocks/<yyyy-mm-dd>-<problem>.md` | Claude mock, Guided Practice, Frank Kane mock, and Hello Interview AI mock summaries (see template below) | Phase 3 and reps |
| `behavioral/log.md` | **One line per behavioral unit, nothing more** | Already exists; BH units add a line |

## Unit types

- **Study** (about 60 min): read the Hello Interview breakdown (and its video walkthrough if it has
  one), then create `system-design/<problem>/notes.md`: key requirements, the deep dives, what surprised you.
- **Redo** (about 60 min): close the breakdown. Start a **45-minute timer**. Talk out loud while
  writing `system-design/<problem>/redo.md` and drawing `system-design/<problem>/<problem>.excalidraw`,
  framework order, requirements first. Then open the breakdown, fill in "What I missed", and commit.
- **Pattern** (about 45 to 60 min): read the pattern page, write 5 to 10 bullets in a new
  `system-design/patterns/<pattern>.md`.
- **Claude mock** (about 60 min): open a new Claude chat and paste:
  > Run a 45-minute system design mock interview: <problem>. Meta E5 calibration. Make me drive
  > with the delivery framework, push back like a real interviewer, then grade each framework step
  > strictly.

  Create `system-design/mocks/<yyyy-mm-dd>-<problem>.md` from the mock summary template below.
- **Guided Practice** (about 45 to 75 min): on the Hello Interview practice page, pick any problem at
  the unit's difficulty that you have not studied or redone yet. Create
  `system-design/mocks/<yyyy-mm-dd>-<problem>.md` from the mock summary template below.
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

## Mock summary template (`system-design/mocks/<yyyy-mm-dd>-<problem>.md`)

```
# <Problem>, <yyyy-mm-dd>, <Claude mock | Guided Practice | Frank Kane mock | HI AI mock>, <minutes> min
- Grade per step: Requirements <>, Core Entities <>, API <>, High-Level Design <>, Deep Dives <>
- Weakest step:
- What the interviewer pushed on:
- One change for next time:
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
