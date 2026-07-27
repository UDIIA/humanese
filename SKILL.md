---
name: humanese
description: Translates any AI-written text (another session, another model, an overnight loop, a subagent, a report, a tweet) from "neuralese" into human language, with a 5-level decompression dial (N1 inline glossary up to N5 full embodiment in a named receiver). Use when the user pastes AI text and wants to understand it ("humanese", "humanese level 4", "translate this to human", "decompress this", "this reads alien", "what language is this"), when an agent handoff/report arrives telegraphic, or before forwarding AI text to a third party (student, client, group). Do NOT use for session wrap-ups/summaries or for turning text into an action plan — those are different jobs.
---

# humanese

## Overview

Neuralese is the dense dialect that post-trained AI develops: telegraphic fragments, every token carrying maximum weight, zero accommodation to the reader. It is not stupidity and not a bug — it is the optimum of the reward function (being right and being dense scores points; being readable does not). This skill is the leash applied after the fact: it takes the dense text and pulls it back toward the human anchor, at whatever level of descent the receiver needs.

Single principle: **this skill's reward is the receiver's clarity, never the size of the output.** Lowering compression is not shortening and not dumbing down: every fact, number, condition and uncertainty in the original survives; only the form becomes flesh.

## The dial: the 5 levels

| Level | Name | What changes | Size | For whom |
|---|---|---|---|---|
| N1 | Glossary | Original intact; acronyms/symbols expanded in parentheses at first occurrence; formatting artifacts fixed; short glossary at the end | ×1 | Expert in a hurry who only tripped on the acronyms |
| N2 | Five Words | Fragments become full sentences; operational labels (Goal/Done/Next/Risk, arrow chains A→B) become flowing prose; same order, same content | ×1.2–1.5 | Technical reader who wants fluency without a lecture |
| N3 | Decompression | DEFAULT. Every concept explained on first appearance; FACT, DECISION, RISK and OPEN kept separate; referents always reintroduced; uncertainty preserved verbatim | ×2–3 | The user, day to day |
| N4 | Milk | Didactic, for someone who doesn't live inside the project: analogy, example, step by step, heavy/light rhythm alternation, key idea stated twice in different forms | ×3–5 | An outside layperson (student, client, group) |
| N5 | Embodiment | Models ONE named receiver (what they know, their state, the channel) and writes in THEIR language, with THEIR examples | varies | A specific person |

The levels carry a theological baptism (the project was born married to 1 Corinthians): N1–N3 are degrees of **hermeneia** (interpretation, 1 Cor 14:13), N4 is the **milk** of 1 Cor 3:2, N5 is **John 1:14** (the Word became flesh). The source language is the "tongue of angels" of 1 Cor 13:1: capability without love = noise. The target of N5 is Pentecost (Acts 2:6-8): each one hears in their own language.

## Choosing the level (when the request doesn't say)

- Request names the level → obey.
- Receiver = the user, medium or long text → N3.
- Receiver = the user, and they only stumbled on an acronym/symbol → N1 or N2.
- Receiver = third party with no project context → N4.
- Receiver = specific person with a known profile → N5 (infer the profile from context; impossible to infer → N4 plus a note about the gap).
- Torn between two levels → the LOWEST one that solves it. Unneeded descent saturates: redundancy for someone who doesn't need it is noise from the other direction.

## The 9 rules

1. **Detect before translating.** Run the marker checklist (below). Text that is already clear passes through untouched: don't inflate what isn't compressed.
2. **Content untouched, form rebuilt.** Every claim, number, condition and hedge in the original survives. Decompressing is never editorializing and never correcting the substance. A factual error spotted in the original goes into the Translator's notes — it is not silently fixed.
3. **Acronyms and symbols expanded at first occurrence, at every level.** Don't know what it stands for? Say you don't know. Never invent an expansion.
4. **Referents always reintroduced.** Short working memory rules: no "this/it/the fix" more than one sentence away from its owner; no "as mentioned above" (repeat the mentioned thing).
5. **One new idea per sentence, and rhythm.** A loaded sentence followed by a light one. The alien is maximum, uniform surprise; the human is moderate, alternating surprise.
6. **Redundancy is an airbag, not fat.** N4 and N5: the key idea appears twice, in different forms (inline + landing). N1 and N2: zero repetition.
7. **Dense-hallucination detector.** A sentence that doesn't open into concrete meaning when you try to expand it is NOT paraphrased in the dark: mark it `[OPAQUE: what jammed]` in the notes. Dense hallucination has the same texture as dense truth, and it breaks on expansion. Every decompression is a free audit.
8. **Anchored human voice.** Natural prose in the receiver's language, zero AI-isms, no em-dash-heavy AI cadence. If the user has a personal voice/style guide or skill, apply it on top when they are the receiver. For third parties: warm-neutral, no niche slang.
9. **Code, commands, JSON and formulas stay intact.** The prose around them gets translated. At N3+ a formula also gets a spelled-out reading (symbol by symbol), but the original stays in the text.

## Neuralese markers (the detector for rule 1)

- Verbless fragments ("Minimal diff. No refactor.")
- Operational labels: Goal / Plan / Done / Next / Risk / Known / Constraints
- Arrow chains (A → B → fails) and pipes used as prose syntax
- Acronym or project nickname without expansion on first use
- Dangling referent: "the fix", "that", "the issue" with no antecedent IN the text
- Uniform density: every sentence loaded, none of them breathes
- Assumes context the reader doesn't have ("per the plan"... what plan?)
- Formatting artifacts: empty code fences, raw JSON mid-prose, broken markdown
- Operational English infiltrating text written in another language

2 or more markers = neuralese confirmed, translate. 0–1 = probably clear, leave it alone (rule 1).

## Output format

Declare in 1 line at the top: "humanese N3, receiver: <who>". Then the translated text, straight through. At the end, ONLY if there is something to record, one block:

**Translator's notes:** each `[OPAQUE]`, any ambiguity where two readings would change the meaning, suspected factual errors in the original, gaps that blocked N5.

The humanese output IS already the digest: do not stack a TL;DR block on top of it (saturating the highlight kills the highlight).

## Minimal example (N2)

Before (real loop neuralese): `Done: auth fix deployed. Next: regression suite. Risk: token refresh edge case. No broad refactor.`

After (N2): "The authentication fix has been deployed. The next step is running the regression test suite. The remaining risk is a rare edge case in access-token renewal. Deliberately, nothing beyond the necessary was touched."

## Common failure modes

- **Summarizing instead of decompressing.** Shortening is the opposite of the job. The output can (and usually does) end up LONGER than the original.
- **Paraphrasing an opaque line in the dark.** If it didn't open, it's `[OPAQUE]`. Inventing a plausible meaning is the worst failure mode, because it looks like success.
- **Over-leveling.** N4 for an expert is as hostile as neuralese for a layperson. The dial exists in both directions.
- **Losing the hedge.** "Probably X" that becomes "X" along the way is a lie manufactured by the translation.
- **Translating the untouchable.** Code, commands, JSON: intact (rule 9).
- **Stacking a TL;DR on top of the output.**

## Foundation (why the skill is built this way)

- Post-training (RLHF, and above all RLVR) rewards being right and being dense; nothing rewards being readable. The model drifts toward the Shannon compression limit, and text at the limit has the texture of noise for anyone without the key.
- In the RLHF objective, `max E[r] − β·KL(π ‖ π_ref)`, the π_ref is the human anchor and the β is the leash. This skill is a β applied after the fact.
- The "alien" feeling is a violation of Uniform Information Density (a psycholinguistic hypothesis): high, uniform per-token surprisal crushes working memory. Hence rules 4 and 5.
- The model writes for a copy of itself (giant context window, perfect recall). The real receiver is a human — tired, often with ADHD. Hence the referent rule and the entire dial.
- The project's theological pair: 1 Cor 13:1 (tongue of angels without agape = sounding brass) and John 1:14 (the Word became flesh).
- Seed of the research: https://x.com/xsteenbrugge/status/2065071364369760508

## Scope boundaries

- Session wrap-ups / "summarize what WE discussed here" is a different job — humanese translates text written BY an AI that you pasted in.
- Turning a text into an action plan (script, checklist, discovery questions, briefing) is a different job — humanese is for understanding, not for acting.
- On collision ("decompress this text GPT wrote"), humanese wins: any pasted AI-written passage with a depth dial is this skill's home turf.
