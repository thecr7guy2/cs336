# How this works — the ritual, explained

Read this if you've forgotten what the commands do or how a session runs.
`README.md` is the design; this is the walkthrough.

---

## Cheat sheet

| command | when | how long |
|---|---|---|
| `/start <topic>` | sitting down | ~6 min |
| `/checkpoint <what happened>` | mid-session, when something confuses or clicks | ~30 sec |
| `/wrap` | before getting up — **mandatory** | ~7 min |
| `/explain <concept>` | anytime you want to test yourself | ~5 min |
| `/review` | once a week | ~30 min |

**If you remember nothing else:** `/start` when you sit down, `/wrap` before you
get up. Everything else is optional. Miss `/wrap` and the day leaves no trace.

---

## What a "command" actually is

Each file in `.claude/commands/` is **just a prompt written down in advance**.
When you type `/wrap`, Claude Code reads `.claude/commands/wrap.md` and injects
its contents into the conversation as instructions.

That's the whole trick. `/wrap` is identical to typing out:

> "Quiz me from memory on today's concept, grade me honestly, then write today's
> journal entry in my voice keeping my wrong turns, update the concept notes with
> a confidence score, and log my open questions."

...every single day, without forgetting a step, without shortening it when
you're tired. **The commands exist so the ritual doesn't depend on your
discipline at 11pm.** You type six characters; the file remembers the other 400
words.

You type them in the chat like a normal message.

---

## One real session, start to end

Say tonight is BPE tokenization and you have an hour.

### `/start BPE tokenization` — ~6 min

I read your last journal entry and scan every concept note that's overdue.

**First, cold quiz.** No notes, no scrolling back:

> **Me:** Last time you implemented the merge loop. Why does BPE merge the *most
> frequent* pair rather than the longest one?
> **You:** uh... because frequent stuff should be one token so it's cheaper?
> **Me:** Close, but that's the goal, not the reason. What's the pair count
> actually measuring? — ⚠️ shaky, dropping `bpe-merges` to 2.

Three to five of those. **Failing one is fine and expected** — that's the system
locating the soft spot, which is the entire job.

**Then FRAME.** I create `journal/2026-08-18.md` and ask three questions, and I
**do not correct any answer**:

> **Me:** Before we open anything — what do you already think you know about BPE?
> **You:** it splits words into subwords somehow, learned from data
> **Me:** Predict: why do LLMs use it instead of just characters, or just words?
> **You:** probably vocab size? words = huge vocab, chars = too many tokens

Your guess goes in the journal **verbatim and uncorrected**. In forty minutes,
when you find out it's also about unseen words and about compute scaling with
sequence length, that recorded guess becomes the "I thought X, actually Y"
moment — which is what your blog is made of. Correcting it now would destroy it.

Then three bullets of plan, and I get out of the way.

### The middle — ~45 min, no commands

You read the paper, you write code, I probe. Normal conversation. I won't write
your implementation; when you're stuck I'll ask what your merge dictionary looks
like after iteration two rather than telling you what's wrong.

**`/checkpoint` is optional, for the interesting moments only:**

> **You:** `/checkpoint i keep getting different merges than the reference and i
> think my pair counting is off by something`

I file it under "where I got stuck" in today's journal, add it to
`questions/open.md`, reply in one line, and shut up. **That's the point** — it
captures the confusion *while you're still inside it*, without derailing you.
Twenty minutes later, once it's fixed, you will no longer be able to reconstruct
what you believed at that moment. That memory is what the blog needs and the one
that evaporates fastest.

Zero checkpoints in a session is fine. Four is fine too.

### `/wrap` — ~7 min, mandatory

> **Me:** Notes closed. Explain BPE to me like I know linear algebra and nothing
> else.

You talk, I don't interrupt. Then I press on the two weakest joints and grade
you *could rebuild it / could describe it / could only name it* — with
specifics, like "you described merging but couldn't say what the algorithm is
greedy about."

Then I write the journal. Your phrasings, your wrong turns, corrections noted
*beside* the original rather than replacing it. I create or update
`concepts/bpe.md` and set confidence from what you **demonstrated**, not what you
claim. Open questions get logged. The entry ends with a specific next move:
*"Next session starts with: make your merge counts match the reference on the
toy corpus."*

### After that hour, on disk

```
journal/2026-08-18.md   your head, today, unedited
concepts/bpe.md         confidence: 2, retest due in 4 days
questions/open.md       🔴 "is the pair count over words or the whole corpus?"
workspace/bpe.py        your code
```

Next time you `/start`, that overdue `bpe.md` is the first thing I quiz you on.
The loop closes itself.

---

## `/explain <concept>` — the standalone self-test

Any time, no session needed. You explain from memory, I find the hole, and the
concept note's confidence gets updated. Useful on a day with 10 free minutes and
no energy for real work.

## `/review` — weekly, ~30 min

Retests everything decayed. Closes questions that quietly answered themselves.
Flags anything that's dropped two weeks running as a *foundation* problem rather
than a memory problem, and schedules a rebuild instead of another retest.
Harvests every `#seed` into `blog/seeds.md`. Writes a retrospective ending with
the honest headline: **are you learning, or accumulating notes?**

---

## Why the pieces are shaped this way

- **Predict before you learn** — a corrected wrong guess encodes far better than
  a clean fact. Hence FRAME, and hence me refusing to correct you during it.
- **Retrieve, don't re-read** — recall builds memory; re-reading builds only
  familiarity. Hence the cold quiz *before* new material, every time.
- **Explain to demonstrate** — you can't fake a mechanism out loud. Hence `/wrap`
  ending with you talking, never with my summary.
- **Catch confusion live** — you lose access to what not-knowing felt like the
  moment you understand. Hence `/checkpoint`, and hence never retrofitting seeds.

**Journal is history** — append-only, never tidied, wrong ideas preserved.
**Concepts are current state** — rewritten from memory, never edited in place.
**Questions are the frontier** — a healthy list always has open items.

## What Claude will and won't do

- **Won't** write the code that is the point of the exercise. Reviews, asks what
  a line does, writes failing tests — doesn't hand you the thing you're learning.
- **Won't** answer straight away when you're stuck. Question → hint → analogy →
  partial → answer, one step per exchange.
- **Will** hand it over instantly if you say **"just tell me"** — no friction, no
  lecture. It gets logged and retested later, that's all.
- **Will** grade honestly. Confidence scores are my judgment of what you
  demonstrated, not your self-report. Memorized-sounding explanations get named.
- **Will** keep your voice in the journal — wrong turns kept, nothing smoothed
  into good prose.

All of that lives in `CLAUDE.md`. If something about how I teach is annoying,
edit that file — it's meant to change as you learn what works for you.
