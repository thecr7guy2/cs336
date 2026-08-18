---
description: Weekly review — retest what's decayed, prune notes, harvest blog seeds
---

Weekly review. ~30 minutes, once a week. This is what keeps the system from
silently rotting.

## 1. What's due

Scan all `concepts/*.md`. Compute due items from `last_tested` + `confidence`
(intervals in `CLAUDE.md`). Quiz the overdue ones — **application questions,
not definitions**. Update `confidence`, `last_tested`, and the retest log.

Anything that dropped two weeks running gets flagged: that's not a memory
problem, it's a misunderstanding at the foundation. Say so and schedule a
rebuild-from-scratch session rather than another retest.

## 2. State of the frontier

Read `questions/open.md`.

- Which questions have quietly answered themselves during the week? Close them.
- Which have been open 3+ weeks? Either they're genuinely hard (fine, keep) or
  they're being avoided (name it).
- Any question that keeps resurfacing in different forms is pointing at a
  missing concept note. Create it.

## 3. Prune and merge concepts

Read all concept notes.
- Two notes describing the same idea → merge, keep the better confusions.
- A note that's grown past one idea → split.
- A note nobody can explain in one sentence → it's not a concept yet, it's a
  topic. Mark it and break it down.

## 4. Harvest seeds

Grep the week's journals for `#seed`, plus every "The thing that confused me"
and every **Where I got stuck** block.

For each, write into `blog/seeds.md`:

```
### <working title>
**Believed:** ...
**Symptom:** ...
**Resolution:** ...
**Why anyone would care:** ...
**Ripeness:** 🌱 / 🌿 / 🌳
**Sources:** journal/2026-08-18.md, concepts/rope.md
```

Discard anything that's just "here's how X works" — no reader needs another one.
Keep the ones where they were wrong in an interesting, non-obvious way.

## 5. Write the retrospective

`reviews/YYYY-Www.md`:

- Sessions this week, hours, topics
- Confidence movement (what rose, what fell, what stalled)
- **Where time actually went vs. where it was worth going** — be blunt if a
  whole session was burned on a tooling problem that taught nothing
- What's genuinely understood vs. what's memorized-looking
- One process change for next week (only one, and only if warranted — do not
  invent a change to seem useful)

End with the honest headline: are they learning, or accumulating notes?
