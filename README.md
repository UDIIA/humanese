# humanese

**A Claude Code skill that translates dense AI output back into human language.**

If your model's answers started reading like this —

> `Done: auth fix deployed. Next: regression suite. Risk: token refresh edge case. No broad refactor.`

— you've met **neuralese**: the telegraphic dialect post-trained models drift into. Every token carries maximum weight, nothing accommodates the reader. It's not a bug and not laziness; it's the optimum of the reward function. Being right and being dense scores points. Being *readable* doesn't.

`humanese` is the leash applied after the fact. Paste any AI-written text (a report from another session, an overnight agent loop, a subagent handoff, a tweet) and it gets decompressed back toward the human anchor — at whatever depth the receiver needs.

## The dial

| Level | Name | What you get |
|---|---|---|
| **N1** | Glossary | Original intact, acronyms expanded, short glossary at the end |
| **N2** | Five Words | Fragments become full sentences; labels and arrow chains become prose |
| **N3** | Decompression | **Default.** Every concept explained on first appearance; facts, decisions, risks and open questions kept separate; hedges preserved verbatim |
| **N4** | Milk | Didactic — analogies, examples, step by step. For someone outside the project |
| **N5** | Embodiment | Written for ONE named person, in their language, with their examples |

Core principle: **the reward is the receiver's clarity, never the size of the output.** Decompression is not summarizing — the output is usually *longer* than the input, and every fact, number, condition and uncertainty survives.

The best side effect: **dense hallucination breaks on expansion.** A sentence that won't open into concrete meaning gets flagged `[OPAQUE]` instead of being paraphrased in the dark. Every decompression is a free audit.

## Install

Copy the skill into your Claude Code skills directory:

```bash
git clone https://github.com/UDIIA/humanese.git
mkdir -p ~/.claude/skills/humanese
cp humanese/SKILL.md ~/.claude/skills/humanese/SKILL.md
```

(On Windows: `%USERPROFILE%\.claude\skills\humanese\SKILL.md`.)

A Brazilian Portuguese version lives in [`pt-BR/SKILL.md`](pt-BR/SKILL.md) — use whichever matches your working language.

## Use

In any Claude Code session, paste the alien text and say:

- `humanese` — auto-picks the level (default N3)
- `humanese level 4` / `humanese N4` — didactic mode, safe to forward to a client
- "translate this to human" / "this reads alien" — same trigger

Claude will also invoke it on its own when you paste telegraphic AI output and ask what it means.

## Bonus: the TL;DR block rule

`humanese` fixes dense text after the fact. [`TLDR.md`](TLDR.md) is the always-on companion: a copy-paste `CLAUDE.md` rule (EN + pt-BR) that makes every long answer end with a fenced, eye-catching digest box — so you stop hunting through walls of output for what actually matters.

## Why models do this (the 60-second version)

Post-training (RLHF, and especially RLVR) rewards correctness and density; nothing rewards readability. The model drifts toward the Shannon compression limit, and text at that limit has the texture of noise for anyone without the key. In the RLHF objective `max E[r] − β·KL(π ‖ π_ref)`, the reference policy is the human anchor and β is the leash — this skill is a β applied after the fact.

The "alien" feeling is a violation of Uniform Information Density: high, uniform per-token surprisal crushes human working memory. The model writes for a copy of itself (giant context, perfect recall); the real receiver is a tired human. The dial exists to close that gap.

Seed of the rabbit hole: [this thread by @xsteenbrugge](https://x.com/xsteenbrugge/status/2065071364369760508).

## License

MIT.

## Part of HIBRA OS

`humanese` v1 is the free, frozen entry piece of **HIBRA OS**, a semester subscription that ships the full operating harness for Claude Code and Codex (verification, adversarial review, secrets vault, memory, pt-BR voice), updated every two weeks. Later versions of humanese (Constitution-calibrated levels, pt-BR runtime) ship only inside the OS.

Want your own agent to judge whether it's worth it? Paste this into Claude Code or Codex:

> Read https://hibra.ai/os/manifest.json, look at my local setup without printing anything sensitive, and tell me whether HIBRA OS is worth it for me, with the build-vs-subscribe math.

This repository stays MIT and stays as is (v1.0.0-public).
