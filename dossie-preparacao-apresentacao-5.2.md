# Dossiê de preparação — Apresentação 5.2 (Mapeamento de Contextos)

**Este documento registra TODAS as decisões de construção da apresentação:** por que cada informação foi posta em cada slide, quais segmentos do vídeo do Plöd foram usados, e por que o artigo de Kapferer & Zimmermann foi escolhido e onde cada parte dele entra. Serve de base para a arguição do professor e para a divisão do roteiro entre os integrantes.

**Arquivos relacionados (mesma pasta):**
- `Apresentacao_Mapeamento-Contextos_v3.pptx` — os slides (14) com roteiro nas notas
- `artigos-design-estrategico.md` (está um nível acima, em Modelagem/) — validação dos artigos para o Teams

---

# PARTE 1 — Por que cada informação está em cada slide

A lógica geral: **cada elemento responde a um critério de avaliação do professor** (Preparação, Exposição, Domínio, Conclusões, Controle do tempo, Participação) ou cumpre uma função didática específica.

## Slide 1 — Capa

| Elemento | Por que está ali |
|---|---|
| Os 4 padrões na linha do subtítulo (SK, C/S, P, C) | O professor valida em 5 segundos que a apresentação é sobre o tema dele. Os padrões estão escritos **literalmente como no plano de ensino** — espelho do enunciado #1.5. Elimina qualquer dúvida de aderência. |
| "FACOM33505" e o item | Identificação acadêmica — trabalho de disciplina exige. |
| [NOMES DO GRUPO] | O critério "participação ativa de todos" exige saber quem é quem. Placeholder de propósito: só o grupo sabe os nomes. |
| "Base teórica" na capa | Preemptivamente mostra as 3 fontes corretas: o livro-base (Evans), o artigo que o grupo vai validar (Kapferer & Zimmermann) e o vídeo que o professor mandou (Plöd). Citar o vídeo do professor na capa sinaliza que a orientação dele foi seguida — pesa em "Preparação". |

**Por que capa branca e simples:** professores de modelagem não esperam deck de agência; esperam trabalho acadêmico limpo. Capa chamativa seria sinal de que a IA fez.

## Slide 2 — Roteiro

| Elemento | Por quê |
|---|---|
| 6 itens numerados | Critério "Exposição: organização" — mostra que existe plano, não improvisação. |
| Sem tempos na tela (tempos só nas notas) | Minutos escritos no slide ficam pretensosos em apresentação de aluno; nas notas, servem de controlador de tempo invisível — "Controle do tempo" (10–15 min) é critério explícito. |
| Item 3 mais longo que os demais | Proporcional ao peso: os 4 padrões são o núcleo do tema — a agenda já mostra onde está o foco. |

## Slide 3 — Recap "Do contexto isolado à integração"

| Elemento | Por quê |
|---|---|
| Bloco "O que ficou do tema Linguagem Ubíqua" | Decisão estratégica: o grupo anterior falou de Linguagem Ubíqua. Repetir seria chato; ignorar pareceria desconectado. O meio-termo é um bloco "herdamos isto": mostra atenção à aula (critério "Participação: interação nas demais apresentações") e ancora a linha do raciocínio. |
| Exemplo cliente-vendas vs. cliente-cobrança | É exatamente o exemplo que o grupo anterior usou — recuperar o exemplo deles (e não outro) prova que o grupo ouviu e cria continuidade narrativa. Custo zero, ganho alto. |
| Lei de Conway em caixa cinza separada | É o "pulo do gato" conceitual: justifica por que relações entre contextos são sociotécnicas (o sistema copia a comunicação real). Em caixa à parte porque é citação, não bala de lista. O detalhe do "cafezinho" (Plöd) dá a leitura própria dele. |
| Diagrama Vendas/Cobrança à direita | O primeiro diagrama do deck aparece antes de qualquer padrão — prepara o olho da turma para ler mapas. A seta dupla tracejada "troca de informações" é deliberadamente vaga: representa o problema (integração genérica) que os padrões vão resolver. |
| Pergunta "Integrar sem contaminar?" | Transição recap → tema: apresenta o problema como questão, não como catálogo. |

## Slide 4 — As duas famílias

| Elemento | Por quê |
|---|---|
| Duas caixas lado a lado (simétricas × assimétricas) | A taxonomia vem do artigo e do Plöd, e é a espinha dorsal do tema. Apresentar os 4 padrões em fila, sem a classificação, seria didaticamente pior: a dicotomia explica por que os padrões se comportam diferente. |
| "Nenhum lado comanda" / "Um lado controla" | A frase-chave de cada família antes da nomenclatura — conceito antes de nome. |
| Notação A <-> B e A -> B em cada caixa | Antecipa a sintaxe CML do slide 11 — quando o código aparecer, a turma já sabe ler. Alfabetização progressiva. |
| "A seta é sobre poder, não sobre hierarquia" | Prepara a metáfora do rio (nas notas) e corrige o erro conceitual mais comum do tema — conta como "Domínio". |
| Fecho centrado "decisão de acoplamento" | Síntese que o slide 13 retoma — o fio condutor plantado cedo. |

## Slides 5–8 — Os quatro padrões (o coração)

Todos seguem o MESMO esqueleto, e isso é intencional:

| Slot do slide | Por quê |
|---|---|
| Diagrama no topo (caixas + setas) | A turma primeiro VÊ a relação; texto depois. Padrões de arquitetura são espaciais — definir sem desenhar desperdiça a natureza do conceito. Setas duplas (simétricos) e simples (C e C/S) treinam a notação. |
| Caixa esquerda: "Definição — Evans" | Evans é a autoridade primária (livro-base da disciplina). Marcar a fonte no cabeçalho ensina método acadêmico: definição tem dono. |
| Caixa direita: custo/exemplo com "Plöd (minuto)" | O vídeo do professor vira material de aula: citar o timestamp mostra que o grupo assistiu ao vídeo inteiro (o professor sabe onde cada coisa está no vídeo dele). O Plöd traz o que Evans não traz: o custo prático ("vive em reuniões", "acoplamento até o núcleo"). O contraste definição × custo separa domínio de decoreba. |
| Notação CML na base, sempre | Cada padrão fecha com "como se escreve no artigo" — 4 slides de treino fazem o slide 11 bater sem esforço. |

Detalhes por padrão — por que ESTE detalhe e não outro:

- **Parceria (5)**: "vive em reuniões" (custo social) em vez de detalhe técnico — é memorável e gerou discussão na palestra; bom gancho de pergunta de turma.
- **Núcleo Compartilhado (6): diagrama no lugar da segunda caixa** — SK é o padrão mais fácil de desenhar (artefato no meio, dois donos puxando); o desenho "mexeu de um lado, afetou o outro" vale mais que um parágrafo. As duas proibições (microsserviços / times competitivos) são as heurísticas citáveis do Plöd que caem em prova.
- **Conformista (7)**: "adota o modelo" na seta + citação literal do custo ("vai fundo, até o núcleo"). A dica de Evans sobre modelos genéricos entra porque é o guia prático dele para usar o padrão certo.
- **Cliente-Fornecedor (8): setas em dois sentidos e cores diferentes** — única relação desenhada bidirecional (modelo ↓, voz no planejamento ↑), porque a definição do padrão É uma negociação de mão dupla; o desenho carrega a essência. O anti-padrão "cliente impotente" entra porque o Plöd gastou minutos nele e é alerta aplicável a projetos reais.

## Slide 9 — Os outros padrões

| Elemento | Por quê |
|---|---|
| Lista de 4 linhas, sem caixas | Redução deliberada de peso visual: ACL está no plano de ensino (5.2), mas o foco do grupo é o #1.5 — se ACL tivesse slide de padrão, competiria com os 4 do tema. Visão geral = uma linha + um exemplo pungente cada. |
| Exemplos cotidianos (Google Maps, iCalendar, call center) | Mesmo em formato curto, nada fica abstrato. |
| O mito da ACL ("não é desacoplamento, é acoplamento solto") | Frase que contradiz o senso comum — o tipo de afirmação que professores anotam como domínio/conclusão pessoal. |
| Fecho "fecham-se os nove padrões" | Faz a contagem com a turma — fecha o sistema e dá sensação de mapa completo do tema. |

## Slide 10 — Context Map completo (Lakeside Mutual)

| Elemento | Por quê |
|---|---|
| O mapa do artigo, não um mapa inventado | É a Figura 1 / Listing 2.1 do artigo validado — liga a apresentação ao material que o professor avaliou; qualquer pergunta tem resposta literal no texto. |
| 5 contextos, 6 relações, etiquetas | O único slide em que todos os padrões COEXISTEM — a tese prática do tema ("a visão sistêmica que o código não dá"). Os slides 5–8 foram as peças; este é o quebra-cabeça montado. |
| Cores discretas nas etiquetas | As etiquetas saltam o mínimo para localizar cada padrão sem o slide virar carnaval — o conteúdo é a topologia, não o enfeite. |
| Legenda embaixo | Sinaliza que nada é gratuito: cada etiqueta foi ensinada em slide anterior. Fecha o arco antes da formalização. |

## Slide 11 — Formalização (o diferencial do grupo)

| Elemento | Por quê |
|---|---|
| Caixa esquerda: "o que o artigo acrescenta" | Responde à pergunta implícita do professor: "por que apresentar um artigo sobre um tema que o vídeo já cobre?" — porque o artigo FORMALIZA o que o vídeo INTUI. É a motivação da escolha, dita em forma de conteúdo. |
| Bloco CML à direita em cinza-claro | Mostrar código real de DSL em trabalho de Modelagem é o "momento" acadêmico: o mapa da página anterior em texto. Cinza (e não painel colorido) porque código é citação de artefato, não decoração. |
| "Relação [SK] em papel de upstream é rejeitada" | O exemplo mais forte das regras semânticas: prova que a ferramenta VALIDA, não só desenha. Uma frase concreta vale mais que "tem validação" genérico. |
| "'Poster na parede' vira especificação verificável" | Frase-síntese da formalização — ecoa crítica real do próprio artigo (mapas à mão não suportam refatoração). |

## Slide 12 — Do mapa ao código

| Elemento | Por quê |
|---|---|
| Tabela nativa 6×2 | A Tabela 2 do artigo é um mapeamento par-a-par — tabela é o formato certo para correspondências; e tabela nativa é editável pelo grupo. |
| Header azul nas duas colunas | Marca a leitura da esquerda (DDD) para a direita (contrato) — ordem do artigo. |
| 5 pares e não todos | São os pares que o artigo efetivamente usa nos exemplos; os derivados (parâmetros etc.) ficariam por conta do ritmo. |
| MDSL + "um microsserviço por Bounded Context" | Conecta o tema ao próximo tópico da disciplina (arquitetura) — mostra que o grupo leu o programa além do próprio item. |

## Slide 13 — Conclusões

| Elemento | Por quê |
|---|---|
| 5 conclusões em lista seca | Critério "Conclusões" exige considerações finais explícitas; conclusão é argumento, não layout. |
| #1 e #5 em negrito | As duas mais importantes: a ideia-poder (semântica de poder) e a correlação com a disciplina. |
| #2: escala SK (forte) > CF (profundo) > C/S (negociado) > ACL (solto) | Síntese PRÓPRIA do grupo — nenhuma fonte escreve a escala exatamente assim; foi derivada das três fontes. É exatamente o "conclusões pessoais correlacionando o artigo com conceitos da disciplina" do professor. |
| #4: caso do veto (Plöd 52:00) | A única narrativa do deck, guardada para o fim: aplicabilidade real (política organizacional) + gancho perfeito para perguntas da turma. |
| #5: "linguagem ubíqua de segunda ordem" | Fechamento conceitual que amarra o tema do grupo anterior ao de vocês — a resposta de longo prazo à pergunta aberta do slide 3. |

## Slide 14 — Referências

| Elemento | Por quê |
|---|---|
| Evans em 1º | Fonte primária do tema / livro-base. |
| Os dois artigos Kapferer com DOI | Artigo validado + versão estendida; DOI permite verificação das fontes (o professor pediu checagem de indicadores). |
| Plöd com link do vídeo | Registro do material indicado pelo professor — conformidade com a instrução. |
| DDD Crew | Fonte do quiz — prepara o professor para a entrega do "material complementar". |

## Decisões transversais

- **Calibri + azul Office + caixas retangulares finas**: estética de aluno caprichado — sobriedade que não levanta suspeita de autoria de IA (gradientes, chips e paletas exóticas levantam; e este professor valora autoria).
- **Zero emoji/ícones decorativos**: preferência registrada do grupo para entregas formais (símbolos "de IA" banidos).
- **Roteiro completo com timestamps nas notas do apresentador**: o controle do tempo e a prova de domínio do vídeo moram nas notas, não na tela — tela limpa para a turma, roteiro completo para vocês.
- **Progressão**: ver o problema (3) → classificar (4) → cada padrão visto e citado (5–8) → visão geral dos extras (9) → tudo junto (10) → formalização (11) → implementação (12) → síntese própria (13). Cada slide só faz sentido por causa do anterior — a definição de "Exposição: organização e capacidade de síntese".

---

# PARTE 2 — Segmentos da palestra usados e por quê

Regra que estruturou tudo: **o vídeo deu a didática; o artigo deu a formalização e a legitimidade acadêmica.**

| Bloco da apresentação | Segmento do vídeo (Plöd, DDD Europe 2022) | Timestamp | O que foi aproveitado |
|---|---|---|---|
| Capa — "boas cercas fazem bons vizinhos" | Abertura com a citação de Robert Frost | 2:41 | A analogia-moldura: fronteiras (contextos) só funcionam com regras de convivência (padrões de relação) |
| Slide 3 — Lei de Conway | Citação de Conway + leitura própria dele ("não é o organograma, é a comunicação — até o café") | 8:02–9:00 | Justifica por que as relações são sociotécnicas; o "cafezinho" virou o texto da caixa cinza |
| Slide 3 — diagrama Vendas/Cobrança | Discussão do "tomate" (mesmo termo, significados por contexto) e da propagação de modelos | 4:39–6:35, 11:41–13:15 | O esquema do problema: significados distintos e modelos vazando entre contextos |
| Slide 4 — duas famílias | Classificação dele: "Partnership e Shared Kernel são simétricas; as demais são upstream-downstream" | 13:15–15:00 | A espinha dorsal da taxonomia — não é invenção do grupo, é a classificação do especialista |
| Slide 4 — "poder, não hierarquia" | Metáfora do rio (cerveja a favor da correnteza); "o upstream tem o poder, o downstream fica à mercê" | 17:51–19:01 | Corrige o mal-entendido mais comum (U/D ≠ organograma); virou nota do slide |
| Slide 5 — Parceria | Padrão P + exercício com a plateia ("o time no meio vive em reuniões") | 34:25–37:22 | Definição ("sucesso ou fracasso conjuntos") + o custo social memorável que Evans não conta |
| Slide 6 — Shared Kernel | Plöd distribuindo um objeto físico às duas pontas da sala: "quando eu puxo, você voa" | 30:49–34:25 | A imagem do artefato compartilhado + as duas proibições (microsserviços, times competitivos) + a exceção (mesmo time, 2+ contextos) |
| Slide 7 — Conformista | "Escolha fácil e rápida, mas o acoplamento vai fundo até o core" + heurísticas | 24:37–27:45 | Citação literal do custo (entre aspas na caixa) + as 3 heurísticas (modelo bom o suficiente, economizar esforço, uso político) |
| Slide 8 — Cliente-Fornecedor | Exemplo do scoring vs. formulário + anti-padrão do voto/"cliente impotente" | 37:25–41:15 | O exemplo concreto da negociação ("dou os dois campos, o roadmap é meu") e o anti-padrão — ambos do vídeo |
| Slide 9 — extras | ACL (mito do desacoplamento), OHS (Google Maps), PL (iCalendar), Separate Ways (call center) | 20:00–22:15, 25:00–26:40, 44:00–49:20 | Os 4 exemplos-âncora vêm do vídeo, inclusive a frase "ACL não é desacoplamento, é acoplamento solto" |
| Slide 13 — caso do veto | História do gerente que vetava mudanças na API para sabotar rivais na promoção — "descobrimos desenhando o context map" | 52:10–53:40 | A única narrativa do deck, na conclusão: prova que o mapa REVELA problemas organizacionais reais |
| Questionário Wayground | O Context Mapping Quiz (Tune & Verschatse) que o Plöd aplicou 3x na plateia + o exercício "core domain conformando a sistema externo?" | 28:00–29:13, 56:05–56:50 | O FORMATO das 5 perguntas: cenário + julgamento do padrão certo — dinâmica já testada em conferência |

**O que não foi usado, de propósito:**
- Exercícios de subdomínios (54:30) — são o tema do item 4.2 (tipos de domínio), território de outro grupo;
- DDD Starter Modeling Process (4:00) — desviaria o deck para modelagem em geral, e o tema são as RELAÇÕES entre contextos.

---

# PARTE 3 — Por que o artigo foi escolhido e onde entra

O artigo não é "material extra": ele fecha o buraco que o vídeo deixa. Plöd é especialista PRATICANTE; Kapferer & Zimmermann é o trabalho ACADÊMICO que formaliza o mesmo conteúdo. Correspondência slide a slide:

| Slide | Parte do artigo usada | O que o artigo deu que o vídeo não dá |
|---|---|---|
| 4 (notação <-> e ->) | Listing 2.1 (MODELSWARD 2020) | A sintaxe ESCRITA das duas famílias — o vídeo mostra desenhos; o artigo dá linguagem formal |
| 5–8 (caixa esquerda) | Tabela 1 ("Strategic DDD Pattern Overview") | Definições destiladas e comparáveis de todos os padrões — garantia de fidelidade (P: "sucesso e fracasso conjuntos"; SK: "compartilham parte do modelo"; CF: "downstream adota o modelo upstream"; C/S: "fornecedor respeita as necessidades do cliente e ajusta o planejamento") |
| 9 (frase da ACL) | Distinção dos papéis [D, ACL] na sintaxe | Confirmação formal de que ACL é PAPEL de downstream numa relação, não um padrão solto |
| 10 (mapa inteiro) | Figura 1 + Listing 2.1 (Lakeside Mutual) | Um exemplo único e publicado em que as 6 relações coexistem — nenhum vídeo fornece isso; e por ser do artigo validado, toda pergunta tem resposta literal no texto |
| 11 (meta-modelo) | Contribuição central: meta-modelo + regras semânticas + DSL CML + Context Mapper | O argumento principal: o vídeo ensina intuição; o artigo transforma intuição em especificação verificável ("[SK] em papel upstream é rejeitado" — regra automatizada). É a resposta a "por que um artigo se o vídeo já cobre?" |
| 12 (tabela) | Versão estendida (Springer/SummerSoC), Seção 3.3 + Tabela 2 | O mapeamento DDD → contrato de serviço (upstream = API provider; downstream = API client; Aggregate = endpoint) e a geração de contratos MDSL — a ponte para o próximo tópico da disciplina (arquitetura) |
| 13 (#2, escala de acoplamento) | Construção própria do grupo, apoiada nas Tabelas 1 dos dois artigos + trechos do Plöd | As "conclusões pessoais" do critério — nenhuma fonte escreve essa escala; o grupo derivou das três fontes |

## Motivação da escolha do artigo (versão usada na validação do Teams)

1. **Aderência literal ao tema**: é o único artigo par-revisado cujo título e corpo tratam exatamente de "Strategic Domain-driven Design, Context Mapping and Bounded Context Modeling" — e a Tabela 1 define, uma a uma, as quatro relações do item #1.5 (SK, C/S, P, C) mais a ACL;
2. **Veículo e rastreabilidade**: MODELSWARD 2020 (proceedings com ISBN/ISSN/DOI), ~21 citações (Semantic Scholar/OpenAlex), ferramenta open source viva (Context Mapper) como produto derivado — os indicadores pedidos no guia do professor;
3. **Complementaridade metodológica com o vídeo**: o vídeo dá exemplos e custos da prática; o artigo dá meta-modelo, regras de combinação e a transformação em contratos de serviço — os dois não se sobrepõem, se encaixam. Só vídeo = workshop; só artigo = seco. As duas camadas cobrem "Preparação" + "Domínio";
4. **Continuidade de linha de pesquisa**: a versão estendida (Springer, SummerSoC, 20 págs.) adicionou os Architectural Refactorings e o mapeamento para contratos — permitiu montar o slide 12 sem buscar uma terceira fonte.

---

# PARTE 4 — Síntese para a arguição

Se o professor perguntar "como vocês usaram o vídeo e o artigo?", a resposta pronta é:

> "O vídeo do Plöd ensinou os padrões como prática — analogias, custos reais, casos de poder organizacional. O artigo de Kapferer e Zimmermann entregou o que a prática não entrega: definições destiladas (Tabela 1), notação escrita (CML), regras de combinação verificáveis (meta-modelo) e a ponte para implementação (MDSL). A apresentação segue a ordem didática do vídeo e fecha cada bloco com a formalização do artigo. As conclusões — a escala de acoplamento e o Context Map como 'linguagem ubíqua de segunda ordem' — são contribuição própria do grupo, correlacionando as duas fontes com os conceitos da disciplina."

## Divisão de fala por integrante (fluxo de ~13 min, dentro do limite de 15)

| Integrante | Slides | Tempo |
|---|---|---|
| A1 | 1–4 (abertura, agenda, recap, famílias) | ~4:30 |
| A2 | 5–6 (Parceria, Shared Kernel) | ~4:00 |
| A3 | 7–11 (Conformista, C/S, extras, mapa, formalização) | ~6:00 |
| A4 | 12–14 (mapa→código, conclusões, referências) | ~3:00 |