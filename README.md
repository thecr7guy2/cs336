# CS336 — Language Modeling from Scratch

Working through Stanford's CS336 end to end: building an LLM from the ground up,
where "from scratch" means PyTorch primitives and nothing else. No HuggingFace
`Trainer`, no `transformers` library, no pre-built tokenizer. If it's the point
of the exercise, it gets written by hand.

**Goal:** understand every layer of the stack well enough to rebuild it from
memory — then turn the whole experience into a blog series.

> **How I'm learning this →** [HOW-IT-WORKS.md](HOW-IT-WORKS.md)
> The daily ritual, the commands, and why the whole thing is shaped that way.
> The framework itself is course-agnostic; this file is the CS336-specific part.

---

## The stack, bottom to top

Everything below has to be built, not imported:

```
tokenizer          bytes → BPE merges → vocab
model              embeddings, RMSNorm, RoPE, attention, SwiGLU, the residual stream
training           cross-entropy, AdamW, LR schedule, grad clipping, checkpointing
systems            profiling, memory accounting, custom kernels, multi-GPU
scaling            what the loss curve does as you spend more, and why
data               where the tokens come from, and why most of them are garbage
alignment          SFT and RL — turning a next-token predictor into something usable
```

## Progress

| unit | topic | status | concepts | code |
|---|---|---|---|---|
| 1 | Tokenization (BPE) | ⬜ not started | — | — |
| 2 | Model architecture | ⬜ | — | — |
| 3 | Training loop & optimizer | ⬜ | — | — |
| 4 | Systems & profiling | ⬜ | — | — |
| 5 | Kernels (Triton / FlashAttention) | ⬜ | — | — |
| 6 | Parallelism & distributed training | ⬜ | — | — |
| 7 | Inference & efficiency | ⬜ | — | — |
| 8 | Scaling laws | ⬜ | — | — |
| 9 | Data curation & filtering | ⬜ | — | — |
| 10 | Alignment (SFT, RLHF/DPO) | ⬜ | — | — |

⬜ not started · 🟨 in progress · ✅ can rebuild from memory

*(Rough shape of the course — check it against the actual syllabus in week one
and correct this table. The assignment lineup shifts year to year.)*

### Assignment 1 — Basics (units 1–3)

Lives in [`workspace/assignment1-basics/`](workspace/assignment1-basics/).
Handout: `cs336_assignment1_basics.pdf`. Environment is already synced.

```sh
cd workspace/assignment1-basics
uv run pytest                    # 46 failing, all NotImplementedError — the starting line
uv run pytest tests/test_train_bpe.py -x   # work one file at a time
```

You implement in `cs336_basics/`, then wire each piece up in `tests/adapters.py`
(21 stubs) — that's the only thing the tests touch. Training data is a separate
download; see the assignment README. It's gitignored, so it stays out of here.

**Suggested order** (each roughly one session): BPE training → tokenizer
encode/decode → Linear + Embedding → RMSNorm → RoPE → attention → SwiGLU →
transformer block → full LM → cross-entropy → AdamW → LR schedule + clipping →
data loader + checkpointing → train a real model on TinyStories.

## Rules I'm holding myself to

1. **No copying.** Not from the reference solution, not from the lecture repo,
   not from another implementation. Read the paper, then write it.
2. **Understand before optimizing.** A slow correct version first, always.
3. **Every bug gets logged** with what I believed at the time. The bug is a
   located misconception, and that's worth more than the fix.
4. **If I can't explain it, I haven't finished it** — tests passing is not the
   bar. Rebuilding it from memory is.
5. **Session gets recorded or it didn't happen.** `/wrap`, every time.

## Repo layout

| path | what |
|---|---|
| `workspace/` | the actual CS336 code — tokenizer, model, training, kernels |
| `journal/` | what I was thinking, daily, unedited |
| `concepts/` | one idea per file, current best understanding + confidence |
| `questions/open.md` | the running list of things I don't get yet |
| `reviews/` | weekly retrospectives and what's due for retest |
| `blog/` | confusions harvested as they happen → drafts |
| `HOW-IT-WORKS.md` | the learning ritual and the commands |
| `CLAUDE.md` | the teaching contract Claude is bound by here |
| `templates/` | forms for journal and concept notes |

## The blog

The end product. Not a rewrite of the lectures — the interesting part of
building an LLM from scratch is never the explanation, it's the two days lost to
a softmax over the wrong axis. Those get captured in `blog/seeds.md` the moment
they happen, because once you understand something you permanently lose access to
what it felt like not to.

## Course

- Stanford CS336 — *Language Modeling from Scratch*
- Lectures, assignments, and the syllabus: <https://stanford-cs336.github.io/>
