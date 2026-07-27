---
name: humanese
description: Traduz qualquer trecho escrito por IA (outra sessao, outro modelo, loop noturno, subagent, relatorio, tweet) de "neuralese" pra lingua humana, com dial de 5 niveis de descompressao (N1 glossario inline ate N5 encarnacao total no receptor). Use quando o usuario colar texto de IA e quiser entender ("humanese", "humanese nivel 4", "traduz pra humano", "descomprime esse trecho", "isso ta alienigena", "que lingua e essa"), quando um handoff/relatorio de agente vier telegrafico, ou antes de encaminhar texto de IA pra terceiro (aluno, cliente, grupo). NAO usar pra fechamento/resumo de sessao nem pra transformar texto em plano de acao (sao trabalhos diferentes).
---

# humanese

## Visão geral

Neuralese é o dialeto denso que IA pós-treinada desenvolve: fragmento telegráfico, cada token carregando peso máximo, zero acomodação ao leitor. Não é burrice nem bug, é o ótimo da função de recompensa (acertar e ser denso dá nota; ser legível não dá). Esta skill é a coleira aplicada depois do fato: pega o texto denso e traz ele de volta pra perto da âncora humana, no nível de descida que o receptor precisa.

Princípio único: **a recompensa desta skill é a clareza do receptor, nunca o tamanho da saída.** Baixar compressão não é encurtar nem burrificar: todo fato, número, condição e incerteza do original sobrevive; só o formato encarna.

## O dial: os 5 níveis

| Nível | Nome | O que muda | Tamanho | Pra quem |
|---|---|---|---|---|
| N1 | Glossário | Original intacto; sigla/símbolo expandido em parênteses na 1ª ocorrência; artefato de formatação consertado; glossário curto no fim | ×1 | Expert com pressa que só tropeçou nas siglas |
| N2 | Cinco Palavras | Fragmento vira frase completa; label operacional (Goal/Done/Next/Risk, setas A→B) vira português corrido; mesma ordem, mesmo conteúdo | ×1,2 a 1,5 | Leitor técnico que quer fluência sem aula |
| N3 | Descompressão | DEFAULT. Cada conceito explicado na 1ª vez; FATO, DECISÃO, RISCO e ABERTO separados; referente sempre reintroduzido; incerteza preservada verbatim | ×2 a 3 | O usuário no dia a dia |
| N4 | Leite | Didático pra quem não vive no projeto: analogia, exemplo, passo a passo, ritmo pesado/leve alternado, ideia-chave dita 2x de formas diferentes | ×3 a 5 | Terceiro leigo (aluno, cliente, grupo) |
| N5 | Encarnação | Modela UM receptor nomeado (o que ele sabe, estado, canal) e escreve na língua DELE, com os exemplos DELE | varia | Pessoa específica |

Batismo teológico dos níveis (o projeto nasceu casado com 1 Coríntios): N1 a N3 são graus de **hermeneía** (interpretação, 1Co 14:13), N4 é o **leite** de 1Co 3:2, N5 é **Jo 1:14** (o Verbo se fez carne). A língua-fonte é a "língua dos anjos" de 1Co 13:1: capacidade sem amor = ruído. O alvo do N5 é Pentecostes (At 2:6-8): cada um ouve na própria língua.

## Escolher o nível (quando o pedido não diz)

- Pedido nomeia o nível → obedecer.
- Receptor = o usuário, texto médio ou longo → N3.
- Receptor = o usuário, e ele só estranhou sigla/símbolo → N1 ou N2.
- Receptor = terceiro sem contexto do projeto → N4.
- Receptor = pessoa específica com perfil conhecido → N5 (inferir o perfil do contexto; impossível inferir → N4 + nota da lacuna).
- Na dúvida entre dois → o MAIS BAIXO que resolve. Descida desnecessária satura: redundância pra quem não precisa dela é ruído do outro lado.

## As 9 regras

1. **Detectar antes de traduzir.** Rodar o checklist de marcadores (abaixo). Texto já claro passa reto: não inflar o que não está comprimido.
2. **Conteúdo intocado, formato refeito.** Toda afirmação, número, condição e hedge do original sobrevive. Descomprimir nunca é opinar nem corrigir o mérito. Erro factual detectado no original vai pras Notas do tradutor, não é consertado em silêncio.
3. **Sigla e símbolo expandidos na primeira ocorrência, em todo nível.** Não sabe o que significa? Diz que não sabe. Nunca inventa expansão.
4. **Referente sempre reintroduzido.** Memória de trabalho curta manda: nada de "isso/ele/o fix" a mais de uma frase de distância do dono; nada de "como mencionado acima" (repete o mencionado).
5. **Uma ideia nova por frase, e ritmo.** Frase carregada seguida de frase leve. O alien é surpresa máxima e uniforme; o humano é surpresa moderada e alternada.
6. **Redundância é airbag, não gordura.** N4 e N5: a ideia-chave aparece duas vezes, em formas diferentes (inline + aterrissagem). N1 e N2: zero repetição.
7. **Detector de alucinação densa.** Frase que não abre em significado concreto quando você tenta expandir NÃO é parafraseada no escuro: marca `[OPACO: o que travou]` nas Notas. Alucinação densa tem a mesma textura da verdade densa, e ela quebra na expansão. Toda descompressão é uma auditoria de graça.
8. **Voz humana ancorada.** Prosa natural na língua do receptor, zero IAismo, zero cadência de travessão de IA. Se o usuário tiver um guia/skill de voz pessoal, aplicar por cima quando ele for o receptor. Receptor terceiro → neutro caloroso, sem gíria de nicho.
9. **Código, comando, JSON e fórmula ficam intactos.** Traduz-se a prosa em volta. Em N3+ a fórmula também ganha leitura por extenso (símbolo a símbolo), mas o original permanece no texto.

## Marcadores de neuralese (o detector do passo 1)

- Fragmento sem verbo ("Minimal diff. No refactor.")
- Label operacional: Goal / Plan / Done / Next / Risk / Known / Constraints
- Cadeia de setas (A → B → falha) e pipes usados como sintaxe de prosa
- Sigla ou apelido de projeto sem expansão na primeira vez
- Referente pendurado: "o fix", "aquilo", "the issue" sem antecedente NO texto
- Densidade uniforme: toda frase carregada, nenhuma respira
- Assume contexto que o leitor não tem ("conforme o plano"... que plano?)
- Artefato de formatação: fence vazio, JSON cru no meio da prosa, markdown quebrado
- Inglês operacional infiltrado em texto pt-BR

2 ou mais marcadores = neuralese confirmado, traduzir. 0 a 1 = provavelmente claro, não mexer (regra 1).

## Formato de saída

Declarar em 1 linha no topo: "humanese N3, receptor: <quem>". Depois o texto traduzido, direto. No fim, SÓ se houver o que registrar, um bloco:

**Notas do tradutor:** cada `[OPACO]`, ambiguidade em que duas leituras mudariam o sentido, erro factual suspeito no original, lacuna que impediu o N5.

A saída de humanese JÁ é o digest: não colar bloco TL;DR em cima (saturar o destaque mata o destaque).

## Exemplo mínimo (N2)

Antes (neuralese real de loop): `Done: auth fix deployed. Next: regression suite. Risk: token refresh edge case. No broad refactor.`

Depois (N2): "O conserto da autenticação foi aplicado. O próximo passo é rodar a bateria de testes de regressão. O risco que sobrou é um caso raro na renovação do token de acesso. De propósito, não mexi em nada além do necessário."

## Erros comuns

- **Resumir em vez de descomprimir.** Encurtar é o oposto do trabalho. A saída pode (e costuma) ficar MAIOR que o original.
- **Parafrasear opaco no escuro.** Se não abriu, é `[OPACO]`. Inventar sentido plausível é o pior modo de falha, porque parece sucesso.
- **Nivelar demais.** N4 pra expert é tão hostil quanto neuralese pra leigo. O dial existe pros dois lados.
- **Perder o hedge.** "Provavelmente X" que vira "X" no caminho é mentira fabricada pela tradução.
- **Traduzir o intocável.** Código, comando, JSON: intactos (regra 9).
- **Colar TL;DR em cima da saída.**

## Fundamento (por que a skill é assim)

- Pós-treino (RLHF, e sobretudo RLVR) recompensa acertar e ser denso; nada recompensa ser legível. O modelo deriva pro limite de compressão de Shannon, e texto no limite tem textura de ruído pra quem não tem a chave.
- Na fórmula do RLHF, `max E[r] − β·KL(π ‖ π_ref)`, o π_ref é a âncora humana e o β é a coleira. Esta skill é um β aplicado depois do fato.
- A sensação "alien" é violação da Densidade Uniforme de Informação (hipótese psicolinguística): surpresa alta e uniforme por token esmaga a memória de trabalho. Daí as regras 4 e 5.
- O modelo escreve pra uma cópia de si mesmo (janela de contexto gigante, recall perfeito). O receptor real é humano, cansado, frequentemente com TDAH. Daí a regra do referente e o dial inteiro.
- Par teológico do projeto: 1Co 13:1 (língua de anjo sem ágape = bronze que soa) e Jo 1:14 (o Verbo se fez carne).
- Semente da pesquisa: https://x.com/xsteenbrugge/status/2065071364369760508

## Fronteiras de escopo

- Fechamento/resumo de sessão ("o que A GENTE discutiu aqui") é outro trabalho: humanese traduz texto escrito POR uma IA que foi colado.
- Transformar texto em plano de ação (roteiro, checklist, discovery, briefing) é outro trabalho: humanese é pra entender, não pra agir.
- Na colisão ("descomprime esse texto que o GPT escreveu"), vale humanese: trecho de IA colado com dial de profundidade é a casa desta skill.
