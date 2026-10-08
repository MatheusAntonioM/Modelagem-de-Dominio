# Roteiro de fala — Apresentação 5.2 (Mapeamento de Contextos) — slide a slide

> **Uso:** cada bloco indica quem fala (A1–A4), o tempo-alvo e o que está na tela. Frases entre aspas são citações literais (Evans, Plöd ou artigo) — fonte conferível no dossiê.
> **Duração total falada:** ~19 min. **Cortes previstos** (marcados por slide) para fechar em 13–14 min, dentro do limite de 15.
> **Trocas de apresentador:** fim do slide 4 (A1→A2), fim do slide 6 (A2→A3), fim do slide 11 (A3→A4) — passe a palavra falando, sem silêncio morto.
> **Arquivos da mesma pasta:** `Apresentacao_Mapeamento-Contextos_v3.pptx` (slides + notas) · `dossie-preparacao-apresentacao-5.2.md` (justificativas) · `artigos-design-estrategico.md` (validação para o Teams).

---

## SLIDE 1 — Capa (A1 · 0:00–0:40)

**Na tela:** título + os 4 padrões (SK, C/S, P, C).

> Bom dia. O nosso tema é o número 1.5: **Design Estratégico com Mapeamento de Relações entre Contextos** — Núcleo Compartilhado, Cliente-Fornecedor, Parceria e Conformista.
>
> Antes de começar, um parágrafo para amarrar com o que veio antes. No tema da Linguagem Ubíqua, o grupo mostrou que cada Bounded Context tem o **seu** significado — o "cliente" de vendas não é o "cliente" de cobrança. Só que o Evans, no livro de 2003, não para aí. Ele também responde à pergunta seguinte: e quando esses contextos **precisam conversar** entre si? Porque, na prática, nenhum sistema vive sozinho. É essa resposta que a gente apresenta hoje.
>
> E a nossa base é a palestra do Michael Plöd, da DDD Europe 2022, que o professor indicou, mais o artigo do Kapferer e do Zimmermann, que a gente validou.

---

## SLIDE 2 — Roteiro (A1 · 0:40–1:00)

**Na tela:** 6 itens numerados.

> A gente vai seguir essa ordem: primeiro o problema — como contextos isolados se integram; depois as duas famílias de relação; em seguida os **quatro padrões** do tema, com exemplo e custo de cada um; e pra fechar, a formalização desses padrões no artigo, como eles viram código, e as nossas conclusões.

*(CORTE POSSÍVEL: este slide pode ser resumido a uma frase se o tempo apertar.)*

---

## SLIDE 3 — Do contexto isolado à integração (A1 · 1:00–3:00)

**Na tela:** bloco do recap + Lei de Conway + diagrama Vendas/Cobrança.

> Recapitulando rápido o que já ficou estabelecido: cada contexto tem vocabulário próprio, e o Bounded Context é a **fronteira** em que aquele modelo e aquela linguagem valem. Fora da fronteira, a mesma palavra vale outra coisa.
>
> Só que sistemas reais **integram**. O financeiro consulta o cadastro, a cobrança puxa dados de vendas. E aí aparece o problema que o tema de hoje resolve: **como juntar mundos diferentes sem um contaminar o modelo do outro?**
>
> O Plöd abre a palestra com uma frase do Robert Frost: *"boas cercas fazem bons vizinhos"*. As cercas são os Bounded Contexts — o tema 1.3 já mostrou isso. Mas cercas boas também precisam de **regras de convivência entre os vizinhos**. E essas regras são os padrões de relação do Context Map.
>
> E tem um fundamento aqui que é importante. O Plöd lembra a **Lei de Conway**: *"qualquer organização que projeta um sistema produz um design que copia a estrutura de comunicação da organização"*. E ele faz uma correção que muita gente erra: Conway não fala do **organograma** — aquela árvore estática. Fala da **comunicação real**: quem fala com quem no dia a dia. Ele vai até dizendo que vale olhar o mapa do andar — quais equipes dividem a mesma cozinha, porque o que se fala na cozinha é comunicação também.
>
> Então as relações entre contextos não são só técnica — são **organizacionais**. Cada seta entre dois contextos é, junto, uma relação entre dois times.

---

## SLIDE 4 — As duas famílias (A1 · 3:00–5:00)

**Na tela:** duas caixas — simétricas × assimétricas.

> O Plöd classifica as relações em **duas famílias**, e essa divisão organiza tudo que vem pela frente.
>
> Primeira família: relações **simétricas**. Nenhum lado comanda o outro — os dois dividem o mesmo destino, ou dividem pedaço do modelo. São dois padrões: a **Parceria** e o **Núcleo Compartilhado**. Na notação do artigo, é a seta dupla, `A <-> B`.
>
> Segunda família: relações **assimétricas**, de *upstream* e *downstream* — a montante e a jusante. Um lado controla o modelo e o outro se adapta. Aqui entram o **Conformista** e o **Cliente-Fornecedor** — e mais os papéis ACL, OHS e PL, que aparecem dentro dessas relações. Notação: seta simples, `A -> B`.
>
> E a metáfora que o Plöd usa pra fixar isso é a do **rio**. Quem está a montante joga uma cerveja no rio — quem está a jusante pega. Quem está a jusante **não consegue devolver**: não manda nada pra montante na contracorrente. Ou seja: o *upstream* muda o modelo e o *downstream* tem que se virar; o caminho inverso não existe. E o Plöd sublinha: isso é dinâmica de **poder** — o upstream tem o poder, e o downstream fica à mercê.

**[TROCA: A1 → A2]**

---

## SLIDE 5 — Parceria (A2 · 5:00–6:45)

**Na tela:** definição Evans + custo Plöd + notação CML.

> Começando pelos simétricos. **Parceria**: o Evans define como contextos cujo sucesso é **interdependente** — ou os dois dão certo juntos, ou os dois **falham juntos**. Não existe uma metade entregue.
>
> Por isso a definição do padrão pede **planejamento coordenado**: as duas equipes têm que gerir a integração e os lançamentos em conjunto. E é bom notar que esse padrão **não aparece no código** — não tem classe, não tem interface. Ele é organizacional.
>
> O custo real, o Plöd mostra com um exercício com a plateia: ele desenha um time no meio, conectado por parcerias a vários outros, e pergunta como é a vida desse time. A resposta que a sala escolheu, e que ele endossa: esse time **"vive em reuniões"** — coordenação atrai coordenação — e o próprio trabalho dele fica pra depois. Dá pra fazer, dá. Mas é a relação mais cara em termos de comunicação.
>
> No artigo, a notação seria: `PolicyManagement <-> [P] RiskManagement` — o gerenciamento de apólicas e o gerenciamento de risco do mesmo sistema de seguros, que só funcionam juntos.

---

## SLIDE 6 — Núcleo Compartilhado (A2 · 6:45–8:45)

**Na tela:** diagrama Contexto A — [parte do modelo] — Contexto B.

> O segundo simétrico é o **Núcleo Compartilhado** — e aqui a demonstração do Plöd é física. Ele pega um cartão, entrega uma "ponta" pra uma pessoa da sala e a outra pra outra, e diz: *"quando eu puxo desse lado, você voa"*.
>
> É isso o Shared Kernel: os dois contextos **compartilham uma parte do modelo** — normalmente como um **artefato** de verdade: uma biblioteca, um *jar*, um esquema de banco em comum, umas *stored procedures*. E esse é, de longe, **o acoplamento mais forte** que o DDD reconhece — mais forte até que o do Conformista, que a gente vai ver. Porque aqui a parte compartilhada é **fisicamente a mesma coisa** nos dois lados: mudou de um lado, **é obrigação** do outro ajustar junto.
>
> Quando evitar, segundo o Plöd e o Evans: **em microsserviços, sempre evitar** — porque ele quebra justamente a independência de *deploy*, que é o motivo de existir do microsserviço. E **entre times em competição, nunca** — o exemplo do Plöd: a montadora com dois fornecedores externos concorrentes; se os dois compartilham o núcleo, aquilo vira palco de jogo político.
>
> O Evans, quando o uso faz sentido, manda: **minimizar**, isolar e **esconder** o núcleo — dar o controle dele a ninguém. E tem uma exceção que o Plöd admite: um **mesmo time** que dono de dois contextos com vocabulário sobreposto — aí o Shared Kernel pode ser o certo. A realidade vale mais que a pureza.

**[TROCA: A2 → A3]**

---

## SLIDE 7 — Conformista (A3 · 8:45–10:30)

**Na tela:** diagrama Upstream → Downstream ("adota o modelo").

> Passando pro lado assimétrico. O **Conformista** é o *downstream* que **adota o modelo do upstream** como se fosse dele — sem tradução, sem camada no meio. O Evans é claro que é uma **decisão explícita**: "nós seguimos a convenção do fornecedor".
>
> O Plöd resume o padrão assim: *"é uma escolha fácil — é rápida"*. Você não gasta nada com tradução, você simplesmente aceita o modelo de fora. **Mas** na sequência ele completa: o acoplamento vai **fundo, até o núcleo** da sua arquitetura. Quando o *upstream* mexe no modelo dele, a mudança atravessa a sua aplicação inteira — não para na borda.
>
> Quando é aceitável? O Plöd dá três heurísticas. Primeira: quando o modelo externo é **bom o suficiente** — bom e estável, não faz diferença ter um modelo próprio. Segunda: pra **economizar o esforço** da tradução — tem situações que a ACL não se paga. E terceira — e essa é interessante — o Conformista também pode ser uma decisão **política**: dar conformismo a um time é **diminuir o poder** dele; tirar é devolver.
>
> O Evans ainda dá um guia prático: conforme-se a **modelos genéricos** — "pessoa", "endereço" — porque o seu diferencial de negócio não está ali; guarde o modelo próprio pro seu núcleo.
>
> Notação: `CustomerCore -> [CF] CustomerSelfService` — com os papéis de upstream, OHS e PL, na esquerda.

---

## SLIDE 8 — Cliente-Fornecedor (A3 · 10:30–12:15)

**Na tela:** diagrama Fornecedor ⇄ Cliente (duas setas: modelo ↓, voz no planejamento ↑).

> O **Cliente-Fornecedor** é a relação assimétrica em que a assimetria fica **negociada**. O Evans define: o fornecedor **respeita** as necessidades do cliente — e, principalmente, **abre espaço pra elas no planejamento**. É a única relação em que o *downstream* consegue **influenciar o roadmap** do *upstream*.
>
> O exemplo do Plöd, com os dois times de banco: o time do **funil de crédito** mantém o formulário de empréstimo — é o *upstream*. O time de **scoring** avalia o risco com base naquele formulário — é o *downstream*. O scoring precisa de **dois campos novos** no formulário. Numa relação U/D pura, ele não teria voz nenhuma. No C/S, os dois negociam, e o acordo sai assim: *"te dou os dois campos — o resto do roadmap é meu"*. O fornecedor continua dono do conjunto, mas o cliente entra na pauta dele.
>
> E o Plöd denomina também o **anti-padrão**: o *cliente impotente*. É o cliente que **não formula requisitos**, não participa — mas, na hora em que o fornecedor precisa mexer, aparece com o **veto**: *"não tenho tempo, o risco é alto"*. Resultado: o fornecedor segue sozinho, sem o cliente na conversa, e o cliente fica à mercê. Pior dos dois mundos — e mais comum do que parece.
>
> Notação: `CustomerSelfService [D, C] <- [U, S] CustomerMgmtContext` — com **D/C** de um lado e **U/S** do outro: o papel de cliente e fornecedor explícito.

---

## SLIDE 9 — Os outros padrões (A3 · 12:15–13:15)

**Na tela:** lista de 4 padrões (ACL, OHS, PL, Separate Ways).

> Uma passada rápida nos outros padrões, porque o Context Map completo usa mais quatro além dos do tema.
>
> A **Camada Anticorrupção** é o contrário do Conformista: o *downstream* **traduz** o modelo do upstream pro próprio modelo — custa o esforço da tradução, mas a mudança externa fica presa na borda. E aqui o Plöd derruba um mito que vale registrar: *"ACL não é desacoplamento — é acoplamento **solto**"*. A relação continua; o que ela limita é o **alcance** do acoplamento.
>
> O **Serviço Aberto** é a API única que um contexto mantém pra **muitos** consumidores ao mesmo tempo — o Google Maps é o exemplo clássico. E quem fornece serviço aberto é quase sempre o *upstream*.
>
> A **Linguagem Publicada** é o vocabulário padrão, **publicado e acessível**, que os contextos assinam — o *iCalendar* é o exemplo: é por causa dele que a Apple, o Google e a Microsoft evoluem os calendários **independentemente**, porque a conversa entre eles é padrão, não modelo de ninguém.
>
> E **Caminhos Separados**: não integrar — por opção ou por custo. O exemplo do Plöd é o agente do call center com cinco telas abertas, copiando e colando na mão — isso é **integração organizacional**, feita por gente, e o mapa precisa mostrar ela também.
>
> Com essas quatro, fecham-se os **nove padrões** de Evans e Vernon.

*(CORTE PARA 13 min: fale só a ACL e o Serviço Aberto, uma linha cada, e a frase final da contagem.)*

---

## SLIDE 10 — O Context Map completo (A3 · 13:15–14:45)

**Na tela:** mapa Lakeside Mutual (5 contextos, 6 relações).

> Esse mapa é o exemplo do artigo validado — o *Lakeside Mutual*, um sistema de seguros fictício. E ele é importante porque é o único momento em que a gente vê **todas as relações funcionando ao mesmo tempo**.
>
> Percorrendo as setas: o **CustomerCore** fornece um Serviço Aberto com Linguagem Publicada pro CustomerMgmt. O **CustomerMgmt** é fornecedor do **CustomerSelfService** — Cliente-Fornecedor. O **CustomerCore** conversa com o **PolicyMgmt** pela Camada Anticorrupção. E o **CustomerSelfService** também **adota o modelo** do CustomerCore — aí está o Conformista. Tem **Núcleo Compartilhado** entre o CustomerSelfService e o PolicyMgmt. E o **PolicyMgmt** e o **RiskMgmt** estão numa **Parceria**.
>
> São as **seis relações** — os quatro padrões do tema, mais OHS/PL e ACL — num **mapa único**. E é isso que o Context Map entrega de valor: a visão sistêmica que **o código não dá**. Cada um de vocês olha o seu repositório e vê o canto dele; o mapa é o único desenho que junta tudo — e é por isso que ele é a ferramenta do **design estratégico**.

*(CORTE PARA 13 min: percorra apenas 4 das 6 relações, priorizando as do tema.)*

---

## SLIDE 11 — Formalização (A3 · 14:45–15:30)

**Na tela:** "o que o artigo acrescenta" + bloco CML.

> E aqui entra o diferencial de usar o artigo. Até agora, tudo que a gente mostrou veio da prática — o Plöd é *coach* de DDD, a autoridade dele vem de anos de consultoria. O artigo do Kapferer e do Zimmermann faz o passo que a prática não faz: **formaliza**.
>
> O artigo destila da literatura um **meta-modelo** dos padrões estratégicos — com **regras semânticas de combinação**: quais combinações **fazem sentido**, e quais não fazem. E essas regras viraram ferramenta: a **DSL do Context Mapper** valida o mapa automaticamente. O exemplo que o próprio artigo usa: declarar `[SK]` — Núcleo Compartilhado — no papel de *upstream* de uma relação é **rejeitado**, porque Shared Kernel é simétrico, por definição. A ferramenta **acusa** o erro.
>
> Ou seja: o Context Map deixa de ser um *"poster na parede"* — frase do próprio artigo sobre os mapas desenhados à mão — e vira uma **especificação que a ferramenta verifica**. É o passo que transforma o desenho em modelo de verdade.

**[TROCA: A3 → A4]**

---

## SLIDE 12 — Do mapa ao código (A4 · 15:30–16:30)

**Na tela:** tabela Context Map → contrato de serviço.

> E da formalização pra implementação, o artigo mostra que a relação entre contextos **vira contrato de serviço**, peça por peça. O *upstream* de uma relação vira o **provedor** da API; o *downstream*, o **cliente**. O *Aggregate* que o *upstream* expõe vira um ***endpoint***; os métodos na raiz do *Aggregate*, as **operações**; e os tipos de dados, os *data types* do contrato.
>
> O Context Mapper **gera** esses contratos — na MDSL, uma linguagem de descrição de API — **direto do mapa**. Ou seja: a relação entre contextos não fica no desenho. Ela vira um **artefato verificável** — e o mapa, além de documentar a comunicação, guia a decomposição: a prática recomendada é **um microsserviço por Bounded Context**. É a ponte do design estratégico pra arquitetura, que a gente vai ver depois na disciplina.

---

## SLIDE 13 — Conclusões (A4 · 16:30–18:30)

**Na tela:** 5 mensagens numeradas.

> Fechando, cinco conclusões.
>
> **Primeira** — e talvez a principal: as relações entre contextos têm **semântica de poder**. Uma seta entre dois contextos nunca é só "o sistema A chama o B". Ela diz quem controla o modelo, quem se adapta a quem, e quem entra no planejamento de quem.
>
> **Segunda**: escolher o padrão é, antes de tudo, decidir o **acoplamento** — e o grupo organizou um espectro: o **Núcleo Compartilhado é o mais forte**, físico; o **Conformista** é profundo, mas sem o compartilhamento de artefato; o **Cliente-Fornecedor** negocia o acoplamento; e a **Camada Anticorrupção** e os padrões de papéis são os mais soltos — limitados à borda.
>
> **Terceira**, duas lições do Plöd que ficam: a ACL **não é desacoplamento** — é acoplamento solto; e um **núcleo de domínio** nunca deveria se conformar com um sistema externo — porque depender da agenda de um fornecedor no seu diferencial de negócio é o pior lugar pra estar.
>
> **Quarta**: o Context Map **revela a comunicação real** — a de Conway — inclusive o que ninguém documenta. O Plöd conta o caso de um gerente que vetava toda mudança numa API pra **travar os times rivais** na disputa de uma promoção — e quem descobriu o jogo foi a equipe que **desenhou o context map**. O mapa expõe política.
>
> **E quinta**, amarrando com a disciplina: a **Linguagem Ubíqua definiu o vocabulário dentro** de cada cerca. O **Context Map é a linguagem entre as cercas** — é a linguagem ubíqua de segunda ordem: o vocabulário dos padrões, com que desenhamos e negociamos as fronteiras. Toda a sequência de temas faz esse arco: contexto, linguagem, e agora **relação**.

*(CORTE PARA 13 min: a lição Fourth (caso do veto) é o corte de emergência — mas é o melhor gancho de perguntas; corte por último.)*

---

## SLIDE 14 — Referências (A4 · 18:30–18:50 + Q&A)

**Na tela:** 6 referências.

> Nossas referências estão aqui: o livro do Evans, os dois artigos do Kapferer e Zimmermann — que validamos com o professor —, a palestra do Plöd, e o material do DDD Crew, que a gente vai usar agora no questionário. Obrigado — e aberto pra perguntas.

---

## Tabela-resumo de tempos

| # | Slide | Quem | Bloco | Completo | Com cortes |
|---|---|---|---|---|---|
| 1 | Capa | A1 | Abertura | 0:40 | 0:30 |
| 2 | Roteiro | A1 | Agenda | 0:20 | 0:15 |
| 3 | Recap + problema | A1 | Abertura | 2:00 | 1:45 |
| 4 | Duas famílias | A1 | Taxonomia | 2:00 | 1:45 |
| 5 | Parceria | A2 | Padrão P | 1:45 | 1:45 |
| 6 | Shared Kernel | A2 | Padrão SK | 2:00 | 2:00 |
| 7 | Conformista | A3 | Padrão C | 1:45 | 1:45 |
| 8 | Cliente-Fornecedor | A3 | Padrão C/S | 1:45 | 1:45 |
| 9 | Outros padrões | A3 | Visão geral | 1:00 | **0:30** (corte) |
| 10 | Mapa completo | A3 | Síntese visual | 1:30 | **1:00** (corte) |
| 11 | Formalização | A3 | Artigo | 0:45 | 0:45 |
| 12 | Do mapa ao código | A4 | Artigo | 1:00 | 1:00 |
| 13 | Conclusões | A4 | Síntese | 2:00 | **1:30** (corte) |
| 14 | Referências | A4 | Encerramento | 0:20 | 0:20 |
| | | | **Total** | **~19:05** | **~15:30 → com cortes agressivos ~13:30** |

## Checklist antes de apresentar

- [ ] Nomes na capa (substituir `[NOMES DO GRUPO]`)
- [ ] Artigo validado com o professor no Teams **antes da data limite**
- [ ] Questionário (5 perguntas, Wayground) pronto e **não divulgado** a ninguém fora do grupo
- [ ] Link de edição do quiz enviado ao professor com antecedência
- [ ] Testar apresentação cronometrada pelo menos 1x em grupo inteiro
- [ ] Salvar export em PDF como backup (o arquivo será anexado à entrega)