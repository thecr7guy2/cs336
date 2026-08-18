---
description: Open a learning session — retrieval quiz on last time, then FRAME
argument-hint: <topic>
---

Start a learning session on: **$1**

Follow `CLAUDE.md`. Budget ~6 minutes for this whole command. Be brisk.

## 1. How long?

Ask, in one line, how many minutes they have today. Size the plan to it:

- **< 30 min** — retrieval + one concept + `/wrap`. No implementation.
- **~60 min** — the standard shape in CLAUDE.md.
- **> 90 min** — add a mid-session checkpoint and a break at the hour.

## 2. Cold retrieval — before anything new

Read the most recent `journal/*.md` and every `concepts/*.md` whose
`last_tested` is overdue per the CLAUDE.md interval table.

Ask **3–5 questions, one at a time**, notes closed:
- 2 from last session's material
- 1–2 from anything overdue
- at least one that requires *applying* the idea rather than restating it
  ("what would break if we removed the residual connection?" not "what is a
  residual connection?")

Grade each honestly. Record verbatim answers — you'll need them for the journal.
Update `confidence` and `last_tested` in the concept notes you tested. A failed
retest drops the score and resets the clock; say so plainly, without consolation.

If this is session #1, skip this section entirely.

## 3. Frame — 3 minutes, before any input

Create `journal/YYYY-MM-DD.md` from `templates/journal.md`.

Ask these three, and **do not answer or correct any of them yet**:

1. What do you already think you know about $1?
2. **Predict:** what do you expect the answer/mechanism to be?
3. What do you want to walk away able to do?

Record their answers *verbatim* in the Frame section. Bad predictions are the
point — do not fix them now. The correction later is what makes it stick.

## 4. Set the plan

State the session plan in 3 bullets max, then get out of the way and begin.
No preamble, no encouragement, no restating what they just said.
