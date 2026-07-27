# The TL;DR block rule

`humanese` is the on-demand fix: you paste alien text, it gets decompressed. This is the **always-on** companion: a rule you paste into your `CLAUDE.md` so every long answer ends with a human-readable digest box your eye can find at a glance.

They attack the same problem from both ends. The skill translates what already came out dense; the rule stops you from ever having to hunt through a long answer for what actually matters.

## Paste this into your `~/.claude/CLAUDE.md`

```markdown
## TL;DR block at the end of long responses

Any long response (more than ~5 lines) ends with a TL;DR block, ALWAYS inside a
triple code fence (hard rule: the fence is what renders the highlighted monospaced
box the eye finds at a glance; emitting it as plain text defeats the entire purpose).
Short responses do NOT get one (saturating the highlight kills the highlight).

CONTENT: clear human prose that preserves intent, facts, decisions, uncertainty,
risks, actions done and pending, choices the user made, and the next step, expanding
jargon and acronyms. Write it for a tired reader catching up, not for a log file.

FORMAT: slice the prose into bullets, each bullet grouping sentences that form one
cohesive unit (1-3 sentences), with a BLANK LINE between bullets. No em-dashes.
No cap on bullet count: as many as the prose needs.

    ━━━━━━━━━━━━━━━━━━━━━━
    ⚡ TL;DR
    • <first cohesive unit, 1-3 sentences>

    • <next cohesive unit>

    • <...as many bullets as the prose needs>
    ━━━━━━━━━━━━━━━━━━━━━━
```

## Versão pt-BR

```markdown
## Bloco TL;DR no fim de resposta longa

Resposta longa (mais de ~5 linhas) termina com bloco TL;DR SEMPRE dentro de cerca
de código tripla (regra dura: é a cerca que renderiza a caixa monoespaçada destacada
pro olho achar de relance; emitir como texto comum quebra o propósito inteiro).
Resposta curta NÃO leva (saturar o destaque mata o destaque).

CONTEÚDO: prosa humana clara que preserva intenção, fatos, decisões, incerteza,
riscos, ações feitas e pendentes, escolhas do usuário e próximo passo, expandindo
jargão e sigla. Escrever pra um leitor cansado se atualizando, não pra um log.

FORMATO: fatiar a prosa em bullets, cada bullet agrupando frases que formam uma
unidade coesa (1 a 3 frases), com LINHA EM BRANCO entre bullets. Sem travessão.
Sem teto de bullets: quantos a prosa pedir.

    ━━━━━━━━━━━━━━━━━━━━━━
    ⚡ TL;DR
    • <primeira unidade coesa da prosa, 1-3 frases>

    • <próxima unidade coesa>

    • <...quantos bullets a prosa pedir>
    ━━━━━━━━━━━━━━━━━━━━━━
```

## Two rules that make it work

1. **The fence is non-negotiable.** The whole point is a visually distinct box for ADHD-friendly, multi-screen scanning. A TL;DR in plain text is just more text.
2. **Short answers get nothing.** If every answer has a highlight box, no answer does.

## One boundary

Never stack this TL;DR on top of a `humanese` output. The humanese translation IS already the digest — see the skill's output-format section.
