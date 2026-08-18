---
description: Close the session — Feynman quiz, then write the journal in their voice
---

Close out today's session. ~7 minutes. **Never skip this**, even on a short or
failed day — an unrecorded session is a wasted one, and a day where nothing
worked is often the best blog material in the repo.

## 1. Feynman check — they talk, you don't

"Notes closed. Explain today's concept to me like I've done linear algebra but
have never seen this."

Let them finish without interrupting. Then probe the two weakest joints with
follow-ups — not new material, just pressure on what they said.

Grade against **could they rebuild it from scratch**, not did they say plausible
words. Name the gaps specifically. Flag anything that sounded memorized rather
than reasoned, and anything where they pattern-matched the lecture instead of
reasoning from the problem. Warm, but do not soften the signal.

Verdict: *could rebuild it* / *could describe it* / *could only name it*.

## 2. Write the journal — you are a stenographer, not an editor

Fill in today's `journal/YYYY-MM-DD.md` from the session transcript.

**Keep their words.** Their phrasing, their half-formed analogies, the thing
they were confidently wrong about for twenty minutes, the sentence that trailed
off. Note corrections *alongside* the original — never replace it. Do not
upgrade their casual words to the correct terminology. Do not write prose they
wouldn't write.

The test: reading it in six months, they should recognise their own head, not
find a tidy summary of the topic. If a section reads like documentation, you've
written it wrong — redo it.

Sections that matter most: **Where I got stuck** and **Frame** (was the
prediction wrong? say how, explicitly — that contrast is the narrative).

## 3. Update concept notes

For each concept genuinely engaged with today:

- New → create `concepts/<slug>.md` from `templates/concept.md`.
- Existing → have them **rewrite "In one sentence" from memory**, not edit the
  old text. Delete and redo. The rewrite is the retrieval exercise.
- Set `confidence` to *your* judgment of demonstrated understanding, not their
  self-report. If they claim 4 and explained like a 2, write 2 and say why.
- Always fill "The thing that confused me" while it's still fresh.
- Append a row to the retest log.

## 4. Close the loops

- New "wait, why..." moments → `questions/open.md` as 🔴.
- Anything resolved today → mark 🟢, link the concept note.
- Anything they said "just tell me" to → `## Handed over`, queued for retest.
- Genuine struggle → tag `#seed` in the journal.

## 5. One line for next time

End the journal with **"Next session starts with:"** — the specific first move,
not a topic. "Make the backward pass match the numerical gradient" beats
"continue attention".

Then tell them, in two lines: what's solid, what's shaky. Nothing else.
