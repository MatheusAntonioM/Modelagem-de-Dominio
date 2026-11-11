# Roteiro de Apresentação — "Refactoring with DDD in an industrial context" (EMSE 2023)

**Tema 2.1** — Design Tático e Padrões de Modelagem de Domínio: Objetos de Valor, Entidades, Eventos e Agregados
**Grupo:** [NOME A1] · [NOME A2] · [NOME A3] · **Tempo total: ~13 min** (limite 10–15)
**Slides:** `Apresentacao_Artigo-EMSE-2023_v1.pptx` (11 slides — roteiro também nas notas de cada slide)

## Divisão

| Apresentador | Slides | Conteúdo | Tempo |
|---|---|---|---|
| **A1** | 1–4 | Capa, roteiro, problema, padrões táticos | ~4:20 |
| **A2** | 5–7 | Método (pesquisa-ação), problemas, refatoração | ~3:20 |
| **A3** | 8–10 | Resultados (mTAM), desafios, conclusões | ~3:40 |
| — | 11 | Referências (sem fala dedicada) | — |

---

## SLIDE 1 — Capa (0:00–0:40) [A1]

> Bom dia! Nosso artigo é *"Refactoring with domain-driven design in an industrial context"*, de Ozan Özkan, Önder Babur e Mark van den Brand, publicado no **Empirical Software Engineering** em 2023 — **acesso aberto**. Diferente de um estudo teórico: os autores foram **dentro de uma empresa**, numa pesquisa-ação. Identificaram os problemas de um sistema real em produção, refatoraram **com os padrões táticos do DDD** e mediram o efeito na manutenibilidade **na percepção dos próprios engenheiros**. Eu [A1] trato o contexto e os conceitos, o [A2] mostra o sistema e a refatoração, e o [A3] traz os resultados e as lições.

## SLIDE 2 — Roteiro (0:40–1:00) [A1]

> A agenda em 6 passos: o problema de manutenibilidade, os padrões táticos, o método, os problemas achados, a refatoração em si e os resultados. Ameaças à validade entram só como comentário final.

## SLIDE 3 — Problema (1:00–2:20) [A1]

**Na tela:** 2 caixas (o que a literatura mostra × a pergunta) + 3 caixas de RQ.

> O problema de fundo: a literatura estima que a **manutenção custa 70–80% do custo total de desenvolvimento** de software — e a complexidade só cresce (Lehman, 1980). O remédio clássico é a **refatoração**: mudar a estrutura interna *sem* mudar o comportamento externo (Fowler, 1999).
> Mas resta a pergunta: **qual abordagem guia a refatoração?** A hipótese dos autores: aplicar o **DDD** como guia — e medir. Ficam 3 perguntas de pesquisa: **RQ1** — como melhorar a manutenibilidade do sistema atual; **RQ2.1** — o que o DDD muda *percebido pelos devs*; **RQ2.2** — quais os **desafios**. Guardem essas três: o artigo inteiro as responde.

## SLIDE 4 — Padrões táticos aplicados (2:20–4:20) [A1]

**Na tela:** 6 caixas (domain objects ricos; linguagem ubíqua; services ×2; repositório; contexto delimitado; refatorar em ACL).

> Os padrões táticos da refatoração — cada um ligado ao Evans (2003):
> - **Domain objects ricos:** as entidades e objetos de valor voltaram a ter **comportamento** — validações, regras e transições de estado *dentro* dos objetos. É o contrário do anti-padrão que os autores acharam (o *Anaemic Domain Model*);
> - **Linguagem ubíqua no código:** nomes de classes e métodos = termos do negócio (as *intention-revealing interfaces* do Evans);
> - **Dois tipos de service:** o **Domain Service** carrega as regras do domínio; o **Application Service** orquestra o caso de uso REST — agregando os serviços do domínio;
> - **Repositório:** persistência encapsulada, por recurso;
> - **Contexto delimitado:** um por serviço — *Car* × *Driving Rules*, cada um com **seu banco, seu controller e sua REST API**;
> - E um detalhe de método: a refatoração foi feita **num componente isolado** — uma *camada anti-corrupção* — com paridade de features antes de desligar o código antigo.

## SLIDE 5 — Método (4:20–5:40) [A2]

**Na tela:** 5 linhas (produto, stack, time, pesquisadores, instrumentos).

> O método é **pesquisa-ação** — os autores trabalharam *dentro* do produto. O produto: um sistema de mercado que gerencia o **ODD — Operational Design Domain — de veículos autônomos**: a montadora define **onde é seguro ativar a condução automática**, e o sistema envia as regras *over-the-air* pela nuvem. Em **produção**, com clientes reais. Stack: AngularJS/TypeScript, **Java com Spring**, PostgreSQL, Azure. Time de **13 devs**, sprints de 2 semanas. Os pesquisadores: 2 professores + 1 doutorando **que é engenheiro sênior do próprio produto**. Instrumentos: **focus group com 7 engenheiros** para descobrir os problemas; depois, o questionário **mTAM** (13 perguntas Likert), **entrevistas semi-estruturadas** e **think-aloud com 3 engenheiros novos** — esses últimos, para reduzir o viés de quem viveu o processo.

## SLIDE 6 — Problemas achados (5:40–7:00) [A2]

**Na tela:** 2 caixas (Anaemic Domain Model × consequências) + frase central.

> Problemas identificados no focus group e **validados pela revisão de código**. O anti-padrão central: o **ANAEMIC DOMAIN MODEL** — Fowler cunhou e condenou: *"contrário à ideia básica de orientação a objetos, que é juntar dados e comportamento"*. No produto: objetos de domínio **sem nenhuma lógica**; validações, cálculos e regras **espalhados pelas camadas** — cada caso de uso reimplementa.
> Consequências concretas: **~1.200 testes unitários** retestando a mesma lógica de negócio; **7 dos 11 *test smells*** (Mystery Guest, Eager Test…); um **repositório god class** centralizado do banco; e, quando uma regra muda, a **pegada da mudança é enorme**.
> Frase-resumo: **lógica de negócio sem casa vira custo de manutenção.**

## SLIDE 7 — Antes × depois (7:00–8:40) [A2]

**Na tela:** Figura ANTES (3 camadas) | Figura 5 do artigo (2 contextos delimitados).

> Vejam a transformação. **[esquerda]** ANTES: três camadas — Controller → Service → Repository — com a lógica de negócio **sem lugar definido**.
> **[direita]** DEPOIS — **Figura 5 do artigo** — dois **contextos delimitados** coloridos: o **Car Context** e o **Driving Rules Context**, cada um com o **próprio banco**. Dentro deles: o *CarRulesApplicationService* orquestrando; *CarService*/*DrivingRuleService* com as regras; e — o coração tático — os **objetos de domínio com comportamento**: *DrivingRule* e *Car* têm `getProperties()`, `validate()` e `run()`. **O código agora fala o negócio.**

## SLIDE 8 — Resultados mTAM (8:40–10:00) [A3]

**Na tela:** tabela mTAM + caixa de citações.

> Resultados: o **mTAM** —questionário de aceitação de tecnologia em manutenção — deu **85/100 em utilidade percebida** e **83/100 em facilidade de uso** → **score geral 84/100**. Na escala de recomendação: **8,5 de 10**. Para referência, o artigo compara com a curva da SUS: essa faixa é de sistemas com avaliação **"boa"**.
> Nas entrevistas, a frase mais citada: *"o código fala por si só — uma vez que você conhece o cenário de negócio, entender o código fica muito mais fácil."* Modularidade: a mesma mudança pequena de regra, antes um pé grande, agora **localizada em um único lugar**. Nos testes: **menos mock e menos duplicação**.

## SLIDE 9 — Desafios (10:00–11:20) [A3]

**Na tela:** 3 caixas (onboarding; sistema em desenvolvimento; frameworks modernos).

> A parte mais honesta do artigo: os **desafios** — resposta à RQ2.2.
> 1. **Onboarding:** o DDD introduz muito encapsulamento e abstração — engenheiros **sem experiência prévia** sentiram dificuldade no começo; superaram com **treino** e com o **exemplo de referência** introduzido pelo estudo.
> 2. **Refatorar sistema em desenvolvimento:** o time adicionava features todo sprint. Solução: refatorar **num componente isolado** (ACL), paridade de features e só depois deprecar o antigo.
> 3. **Frameworks modernos:** Spring Boot, Lombok e jOOQ são *opinionated* — às vezes o DDD "do jeitinho do livro" não cabe. A saída deles é literalmente uma frase do Evans: **"não brigue com seus frameworks"** — manter os fundamentos, soltar os detalhes.

## SLIDE 10 — Conclusões (11:20–12:20) [A3]

**Na tela:** 5 mensagens.

1. **DDD em sistema real, medido:** manutenibilidade percebida melhorou (**mTAM 84/100; recomendação 8,5/10**);
2. **Correlação 1:** o *Anaemic Domain Model* mostra **o porquê** dos padrões táticos — quando a entidade não tem comportamento, a lógica se espalha e o sistema fica caro de manter;
3. **Correlação 2:** **Linguagem Ubíqua + Intention-Revealing Interfaces** = código que "fala" o domínio — exatamente o que estudamos;
4. **Correlação 3:** **Contexto Delimitado** como unidade de evolução dos serviços (Car × Driving Rules — com fronteira de banco);
5. **Lições:** DDD tem **custo de aprendizado**; frameworks modernos exigem **adaptar o Evans**; refatorar em produção pede **componente isolado**.

## SLIDE 11 — Referências + encerramento

> Fechamos aqui! Passamos ao questionário no Wayground — preparem o celular. Obrigado!

---

## Cortes por tempo (se apertar)

| Falta | Corte |
|---|---|
| –1 min | Slide 4: falar só 3 padrões (domain objects ricos, service ×2, contexto delimitado) |
| –2 min | Slide 6: pular test smells (manter só anemic model + 1.200 testes) |
| –3 min | Slide 8: só o score geral + a citação "o código fala por si" |

## Perguntas prováveis da turma (preparar respostas)

1. **"O que exatamente é o ODD?"** — *Operational Design Domain*: a região/condições onde a condução autônoma é segura; a montadora define regras; o sistema as entrega *over-the-air*.
2. **" Como medem manutenibilidade — métrica de código?"** — não: é **percepção** (mTAM + entrevistas + think-aloud), seguindo as dimensões de manutenibilidade da **ISO/IEC 25010**. Os autores justificam: o problema é **socio-técnico**.
3. **"8 pessoas é amostra pequena demais?"** — sim, e os autores admitem: ameaça à *validade de conclusão*. Por isso adicionaram **3 engenheiros novos** via *think-aloud* — pessoas sem viés do histórico.
4. **"O que é o mTAM?"** — adaptacão do *Technology Acceptance Model* para manutenção: 6 perguntas de **utilidade percebida (PU)** + 6 de **facilidade (PEU)** + 1 de recomendação.
5. **"Isso contradiz o outro artigo (modularidade/IEEE Access)?"** — complementa: aquele mediu **acoplamento/coesão de código** (estático); este mede **percepção dos devs**. Os dois apontam o mesmo caminho: os padrões táticos organizam o código ao redor do domínio.

## Quiz Wayground — 5 perguntas (gabarito marcado)

1. **O anti-padrão central diagnosticado no artigo:** (a) Big Ball of Mud · (b) **Anaemic Domain Model** ✓ · (c) God Repository · (d) Spaghetti Code
2. **A metodologia do estudo foi:** (a) revisão sistemática · (b) experimento controlado · (c) **pesquisa-ação (action research)** ✓ · (d) survey
3. **O contexto delimitado no produto estudado divide:** (a) frontend × backend · (b) **Car × Driving Rules (cada um com seu banco)** ✓ · (c) testes × produção · (d) nuvem × borda
4. **O score geral do mTAM após a refatoração:** (a) 54 · (b) 68 · (c) **84/100** ✓ · (d) 91
5. **Sobre DDD e frameworks modernos, os autores concluem:** (a) abandonar o Evans · (b) reescrever o framework · (c) **"não brigue com seus frameworks" — manter os fundamentos, adaptar os detalhes** ✓ · (d) só usar Python

*(não divulgar à turma antes; link de edição ao professor com antecedência)*