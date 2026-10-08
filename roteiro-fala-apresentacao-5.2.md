# Roteiro de fala — Apresentação 5.2 (Mapeamento de Contextos) — slide a slide

> **Uso:** cada bloco indica quem fala (A1–A4), o tempo-alvo e o que está na tela. As frases entre aspas são citações literais (de Evans, do Plöd ou do artigo) — as fontes estão conferíveis no dossiê, com timestamp.
> **Duração falada completa:** cerca de 19 minutos. Os **cortes previstos** (marcados em cada slide) fecham em 13–14 minutos, dentro do limite de 15.
> **Trocas de apresentador:** fim do slide 4 (A1→A2), fim do slide 6 (A2→A3), fim do slide 11 (A3→A4). Passe a palavra falando, no fim do seu último parágrafo, sem silêncio morto.
> **Arquivos desta pasta:** `Apresentacao_Mapeamento-Contextos_v3.pptx` (slides com notas) · `dossie-preparacao-apresentacao-5.2.md` (justificativas de cada decisão) · `artigos-design-estrategico.md` (validação para o Teams).

---

## SLIDE 1 — Capa (A1 · 0:00–0:40)

**Na tela:** título + os 4 padrões (SK, C/S, P, C).

> Bom dia. O nosso tema é o de número 1.5: **Design Estratégico com Mapeamento de Relações entre Contextos** — Núcleo Compartilhado, Cliente-Fornecedor, Parceria e Conformista.
>
> Antes de começar, um parágrafo para amarrar com o que veio antes. No tema da Linguagem Ubíqua, o grupo anterior mostrou que cada Bounded Context carrega o **próprio** significado — o "cliente" de vendas não é o "cliente" de cobrança. Só que o Evans, no livro de 2003, não para aí. Ele também responde à pergunta seguinte: **e quando esses contextos precisam conversar entre si?** Porque, na prática, nenhum sistema vive sozinho. É essa resposta que a gente apresenta hoje.
>
> A nossa base tem duas fontes: a palestra do Michael Plöd, da DDD Europe 2022, que o professor indicou; e o artigo do Kapferer e do Zimmermann, que a gente validou.

*(Dica de cena: ao dizer os nomes dos 4 padrões, aponte para eles no slide, um a um, na ordem.)*

---

## SLIDE 2 — Roteiro (A1 · 0:40–1:00)

**Na tela:** 6 itens numerados.

> A gente vai seguir essa ordem: primeiro, o problema — como contextos isolados se integram; depois, as duas famílias de relação; em seguida, os **quatro padrões** do tema, cada um com definição, exemplo e custo; e, para fechar, a formalização desses padrões no artigo, a conversão deles em código, e as nossas conclusões.

*(CORTE POSSÍVEL: se o tempo apertar, este slide vira uma única frase — "seguimos do problema até os quatro padrões e a formalização no artigo".)*

---

## SLIDE 3 — Do contexto isolado à integração (A1 · 1:00–3:00)

**Na tela:** bloco do recap + Lei de Conway + diagrama Vendas/Cobrança.

> Recapitulando rápido o que já está estabelecido: cada contexto tem vocabulário próprio, e o Bounded Context é a **fronteira** dentro da qual aquele modelo e aquela linguagem valem. Fora da fronteira, a mesma palavra vale outra coisa.
>
> Só que sistemas reais **se integram**. O financeiro consulta o cadastro; a cobrança puxa dados de vendas. Aí aparece o problema que o tema de hoje resolve: **como juntar mundos diferentes sem que um contamine o modelo do outro?**
>
> O Plöd abre a palestra com uma frase do Robert Frost: *"boas cercas fazem bons vizinhos"*. As cercas são os Bounded Contexts — o tema 1.3 já mostrou isso. Mas cercas boas também precisam de **regras de convivência entre os vizinhos**. E essas regras são exatamente os padrões de relação do Context Map.
>
> Um fundamento here é importante — a **Lei de Conway**, que o Plöd cita: *"qualquer organização que projeta um sistema produz um design que copia a estrutura de comunicação da organização"*. E ele faz uma correção que muita gente erra: Conway não fala do **organograma** — aquela árvore estática. Fala da **comunicação real**: quem conversa com quem no dia a dia. Ele vai além e sugere até olhar a planta do andar — quais equipes dividem a mesma cozinha —, porque o que se conversa na cozinha também é comunicação.
>
> Então, as relações entre contextos não são só técnicas: são **organizacionais**. Cada seta entre dois contextos é, ao mesmo tempo, uma relação entre dois times.

---

## SLIDE 4 — As duas famílias (A1 · 3:00–5:00)

**Na tela:** duas caixas — simétricas × assimétricas.

> O Plöd classifica as relações em **duas famílias**, e essa divisão organiza tudo o que vem pela frente.
>
> Primeira família: relações **simétricas**. Nenhum lado comanda o outro — os dois dividem o mesmo destino, ou dividem um pedaço do modelo. São dois padrões: a **Parceria** e o **Núcleo Compartilhado**. Na notação do artigo, é a seta dupla: `A <-> B`.
>
> Segunda família: relações **assimétricas**, de *upstream* e *downstream* — a montante e a jusante. Um lado controla o modelo; o outro se adapta. Aqui entram o **Conformista** e o **Cliente-Fornecedor** — e, dentro delas, os papéis ACL, OHS e PL. Notação: seta simples, `A -> B`.
>
> Para fixar, a metáfora que o Plöd usa é a do **rio**. Quem está a montante joga uma cerveja no rio; quem está a jusante pega. E quem está a jusante **não consegue devolver** — nada sobe na contracorrente. Em software: o *upstream* muda o modelo e o *downstream* precisa se adaptar; o caminho inverso não existe. E o Plöd sublinha: isso é dinâmica de **poder** — o upstream detém o poder, e o downstream fica à mercê.

**[TROCA: A1 → A2]**

---

## SLIDE 5 — Parceria (A2 · 5:00–6:45)

**Na tela:** definição Evans + custo Plöd + notação CML.

> Começando pelos simétricos. **Parceria**: o Evans a define como a relação entre contextos cujo sucesso é **interdependente** — ou os dois dão certo juntos, ou os dois **falham juntos**. Não existe "metade entregue".
>
> Por isso, a definição do padrão exige **planejamento coordenado**: as duas equipes têm de gerir a integração e os lançamentos em conjunto. E vale observar: esse padrão **não aparece no código** — não tem classe, não tem interface. Ele é puramente organizacional.
>
> O custo real o Plöd revela com um exercício de plateia: ele desenha um time ao centro, conectado por parcerias a vários outros, e pergunta como é a vida desse time. A resposta que a sala escolheu — e que ele endossou — é: esse time **"vive em reuniões"** — coordenação atrai mais coordenação —, e o próprio trabalho dele fica para depois. Dá para operar assim; somente é a relação mais cara em comunicação.
>
> No artigo, a notação seria: `PolicyManagement <-> [P] RiskManagement` — o gerenciamento de **apólices** e o de **risco** no mesmo sistema de seguros, que só funcionam juntos.

---

## SLIDE 6 — Núcleo Compartilhado (A2 · 6:45–8:45)

**Na tela:** diagrama Contexto A — [parte do modelo] — Contexto B.

> O segundo simétrico é o **Núcleo Compartilhado** — e a demonstração do Plöd é física. Ele pega uma "ponte" (uma barra) e entrega uma ponta a uma pessoa de um lado da sala, e a outra ponta a alguém do lado oposto; quando uma puxa, a outra sente: *"quando eu puxo desse lado, você voa"*.
>
> É isso o Shared Kernel: os dois contextos **compartilham uma parte do modelo** — tipicamente como um **artefato** concreto: uma biblioteca (*jar*, DLL, módulo npm), um esquema de banco em comum, *stored procedures*. É o **acoplamento mais forte** que o DDD reconhece — mais forte até do que o do Conformista, que veremos depois. Aqui a parte compartilhada é **fisicamente a mesma coisa** dos dois lados: se muda de um lado, o outro **tem a obrigação** de ajustar junto.
>
> Quando evitar — segundo o Plöd e o Evans: **em microsserviços, sempre evitar**, porque quebra justamente a independência de *deploy*, que é a razão de ser do microsserviço; e **entre times concorrentes, nunca** — o exemplo do Plöd é a montadora com dois fornecedores externos concorrentes: se os dois compartilham o núcleo, esse núcleo vira palco de jogo político.
>
> Quando o uso faz sentido, o Evans diz o que fazer: **minimizar** o que é compartilhado, **isolar** e **esconder** o núcleo — e nunca dar o controle dele a alguém de fora. E há uma exceção que o Plöd admite: quando **um mesmo time é dono** de dois contextos com vocabulário sobreposto — aí o Shared Kernel pode ser a escolha certa. A realidade vale mais que a pureza.

**[TROCA: A2 → A3]**

---

## SLIDE 7 — Conformista (A3 · 8:45–10:30)

**Na tela:** diagrama Upstream → Downstream ("adota o modelo").

> Passando ao lado assimétrico: o **Conformista** é o *downstream* que **adota o modelo do upstream** como se fosse dele — sem tradução, sem camada no meio. O Evans deixa claro que é uma **decisão explícita**: "nós seguimos a convenção do fornecedor".
>
> O Plöd resume o padrão assim: *"é uma escolha fácil — é rápida"*. Não se gasta nada com tradução; simplesmente se aceita o modelo de fora. **Mas** ele completa na sequência: o acoplamento vai **fundado, até o núcleo** da sua arquitetura. Quando o *upstream* muda o modelo dele, a mudança atravessa toda a sua aplicação — não para na borda.
>
> Quando é aceitável? O Plöd dá três heurísticas. Primeira: quando o modelo externo é **bom o suficiente** — bom e estável; um modelo próprio não agregaria nada. Segunda: para **economizar o esforço da tradução** — há situações em que o custo da camada não se paga. Terceira — e essa é curiosa —, o Conformista também pode ser uma decisão **política**: conceder o conformismo a um time é **reduzir o poder** dele; retirar, é devolver.
>
> O Evans ainda dá um guia prático: conforme-se a **modelos genéricos** — "pessoa", "endereço" —, porque o diferencial do seu negócio não está ali; o modelo próprio fica reservado ao seu núcleo.
>
> Notação: `CustomerCore -> [CF] CustomerSelfService` — com os papéis e padrões do lado do upstream marcados: U, OHS e PL.

---

## SLIDE 8 — Cliente-Fornecedor (A3 · 10:30–12:15)

**Na tela:** diagrama Fornecedor ↔ Cliente — duas setas: modelo (→) e voz no planejamento (←).

> O **Cliente-Fornecedor** é a relação assimétrica em que a assimetria é suavizada pela **negociação**. O Evans define: o fornecedor **respeita** as necessidades do cliente — e, principalmente, **abre espaço para elas no próprio planejamento**. É a única relação em que o *downstream* influencia o *roadmap* do *upstream*.
>
> O exemplo do Plöd usa dois times de banco: o time do **funil de crédito** mantém o formulário de empréstimo — é o *upstream*. O time de **scoring** avalia o risco com base naquele formulário — é o *downstream*. O scoring precisa de **dois campos novos** no formulário. Numa relação de monteante e jusante pura, ele não teria voz alguma. No C/S, os dois negociam, e o acordo sai assim: *"te dou os dois campos — o resto do *roadmap* é meu"*. O fornecedor segue dono do seu conjunto, mas o cliente entra na pauta.
>
> O Plöd também batiza o **anti-padrão**: o *cliente impotente*. É o cliente que **não formula requisitos** nem participa — mas, quando o fornecedor precisa mudar, aparece com o **veto**: *"não tenho tempo; o risco é alto"*. Resultado: o fornecedor caminha sozinho, sem escuta do cliente, e o cliente fica à mercê. Pior dos dois mundos — e mais comum do que parece.
>
> Notação: `CustomerSelfService [D, C] <- [U, S] CustomerMgmtContext` — de um lado, **D/C** (downstream, cliente); do outro, **U/S** (upstream, fornecedor). Os papéis ficam explícitos.

---

## SLIDE 9 — Os outros padrões (A3 · 12:15–13:15)

**Na tela:** lista de 4 padrões (ACL, OHS, PL, Separate Ways).

> Uma passada rápida nos outros padrões — o Context Map completo usa mais quatro além dos do tema.
>
> A **Camada Anticorrupção** é o contrário do Conformista: o *downstream* **traduz** o modelo do upstream para o próprio modelo. Custa o esforço da tradução, mas a mudança externa fica presa na borda. Aqui, o Plöd derruba um mito que vale registrar: *"a ACL não é desacoplamento — é acoplamento **solto**"*. A relação continua; o que a camada limita é o **alcance** do acoplamento.
>
> O **Serviço Aberto (Open Host Service)** é a API única que um contexto mantém para **muitos** consumidores ao mesmo tempo — o Google Maps é o exemplo clássico. E quem fornece um serviço aberto é quase sempre o *upstream*.
>
> A **Linguagem Publicada** é o vocabulário padrão, **publicado e acessível**, que os contextos assinam. O exemplo é o *iCalendar*: é por causa dele que Apple, Google e Microsoft evoluem os calendários **independentemente** — a conversa entre eles é um padrão, e não o modelo de ninguém.
>
> E **Caminhos Separados (Separate Ways)**: não integrar — por opção ou por custo. O exemplo do Plöd é o agente de call center com cinco telas abertas, copiando e colando à mão: é **integração organizacional**, feita por pessoas — e o mapa precisa registrá-la também.
>
> Com essas quatro, fecham-se os **nove padrões** de Evans e Vernon.

*(CORTE PARA 13 min: fale somente a ACL e o Serviço Aberto, uma linha cada, e a frase final da contagem.)*

---

## SLIDE 10 — O Context Map completo (A3 · 13:15–14:45)

**Na tela:** mapa Lakeside Mutual (5 contextos, 6 relações).

> Este mapa é o exemplo do artigo validado — o **Lakeside Mutual**, um sistema de seguros fictício. Ele importa porque é o único momento em que veremos **todas as relações funcionando ao mesmo tempo**.
>
> Percorrendo as setas:
> - o **CustomerCore** fornece um Serviço Aberto com Linguagem Publicada para o **CustomerMgmt**;
> - o **CustomerMgmt** é fornecedor do **CustomerSelfService** — aí está o Cliente-Fornecedor;
> - o **CustomerCore** também fornece para o **CustomerSelfService**, que **adota o modelo** dele — aí está o Conformista;
> - o **CustomerCore** fornece para o **PolicyMgmt**, que o protege com uma **Camada Anticorrupção**;
> - há um **Núcleo Compartilhado** entre o **CustomerSelfService** e o **PolicyMgmt**;
> - e o **PolicyMgmt** e o **RiskMgmt** formam uma **Parceria**.
>
> São **seis relações** — os quatro padrões do tema, mais OHS/PL e ACL — em um **único mapa**. E é daqui que vem o valor do Context Map: a visão sistêmica **que o código não dá**. Cada time, olhando para o próprio repositório, enxerga só o seu pedaço; o mapa é o único desenho que junta tudo — e por isso é a ferramenta do **design estratégico**.

*(CORTE PARA 13 min: percorra apenas 4 das 6 relações, priorizando as do tema.)*

---

## SLIDE 11 — Formalização no artigo (A3 · 14:45–15:30)

**Na tela:** "o que o artigo acrescenta" + bloco CML.

> Aqui entra o diferencial de apresentar o artigo. Até agora, tudo veio da prática — o Plöd é *coach* de DDD, e a autoridade dele vem dos anos de consultoria. O artigo do Kapferer e do Zimmermann dá o passo que a prática não dá: **formaliza**.
>
> O artigo destila da literatura um **meta-modelo** dos padrões estratégicos — com **regras semânticas de combinação**: quais combinações **fazem sentido**, e quais não fazem. E essas regras viraram ferramenta: a **DSL do Context Mapper** valida o mapa automaticamente. O exemplo do próprio artigo: declarar `[SK]` — Núcleo Compartilhado — no papel de *upstream* de uma relação é **rejeitado**, porque o Shared Kernel é simétrico, por definição. A ferramenta **acusa** o erro.
>
> Ou seja: o Context Map deixa de ser um *"poster na parede"* — é a expressão do próprio artigo sobre os mapas desenhados à mão — e vira uma **especificação que a ferramenta verifica**. É o que transforma o desenho em modelo de verdade.

**[TROCA: A3 → A4]**

---

## SLIDE 12 — Do mapa ao código (A4 · 15:30–16:30)

**Na tela:** tabela Context Map → contrato de serviço.

> E da formalização vem a implementação: o artigo mostra que a relação entre contextos **vira contrato de serviço**, peça por peça. O *upstream* da relação vira o **provedor** da API; o *downstream*, o **cliente** da API. O *Aggregate* que o *upstream* expõe vira um ***endpoint***; os métodos da raiz do *Aggregate*, as **operações**; e os tipos de dados, os *data types* do contrato.
>
> O Context Mapper **gera** esses contratos — na MDSL, uma linguagem de descrição de APIs — **diretamente do mapa**. Ou seja: a relação entre contextos não fica presa ao desenho; ela vira um **artefato verificável**. E o mapa, além de documentar a comunicação, guia a decomposição: a prática recomendada é **um microsserviço por Bounded Context**. É a ponte do design estratégico para a arquitetura — que veremos adiante na disciplina.

---

## SLIDE 13 — Conclusões (A4 · 16:30–18:30)

**Na tela:** 5 mensagens numeradas.

> Fechando, cinco conclusões.
>
> **Primeira** — talvez a principal: as relações entre contextos têm **semântica de poder**. Uma seta entre dois contextos jamais é só "o sistema A chama o B". Ela diz quem controla o modelo, quem se adapta a quem, e quem entra no planejamento de quem.
>
> **Segunda**: escolher o padrão é, antes de tudo, uma decisão de **acoplamento** — e o grupo o organizou num espectro: o **Núcleo Compartilhado é o mais forte**, físico; o **Conformista** é profundo, mas sem o compartilhamento do artefato; o **Cliente-Fornecedor** negocia o acoplamento; e a **Camada Anticorrupção** e os padrões de papéis são os mais soltos — limitados à borda.
>
> **Terceira**, duas lições do Plöd que ficam: a ACL **não é desacoplamento** — é acoplamento solto; e um **núcleo de domínio** jamais deveria se conformar a um sistema externo — porque o núcleo é o diferencial do negócio, e depender lá da agenda de um fornecedor é o pior cenário possível.
>
> **Quarta**: o Context Map **revela a comunicação real** — a de Conway —, inclusive o que ninguém documenta. O Plöd conta o caso de um gerente que vetava toda mudança numa API para **travar os times rivais** na disputa de uma promoção — e quem descobriu o jogo foi a equipe que **desenhou o context map**. O mapa expõe política.
>
> **E quinta**, amarrando com a disciplina: a **Linguagem Ubíqua definiu o vocabulário dentro** de cada cerca. O **Context Map é a linguagem entre as cercas** — a linguagem ubíqua "de segunda ordem": o vocabulário dos padrões com o qual desenhamos e negociamos as fronteiras. A sequência de temas forma este arco: contexto, linguagem — e agora **relação**.

*(CORTE PARA 13 min: a Quarta (caso do veto) é o corte de emergência — mas é o melhor gancho para as perguntas; corte por último.)*

---

## SLIDE 14 — Referências (A4 · 18:30–18:50 + perguntas)

**Na tela:** 6 referências.

> Nossas referências estão na tela: o livro do Evans; os dois artigos do Kapferer e do Zimmermann, que validamos com o professor; a palestra do Plöd; e o material do DDD Crew, que a gente usará agora no questionário. Obrigado — e ficamos à disposição para as perguntas.

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
| | | | **Total** | **~19:05** | **~13:30–14:00** |

## Checklist antes de apresentar

- [ ] Nomes na capa (substituir `[NOMES DO GRUPO]`)
- [ ] Artigo validado com o professor no Teams **antes da data limite**
- [ ] Questionário (5 perguntas, Wayground) pronto e **não divulgado** a ninguém fora do grupo
- [ ] Link de edição do quiz enviado ao professor com antecedência
- [ ] Ensaio cronometrado pelo menos uma vez com o grupo inteiro
- [ ] Exportar em PDF como backup (o arquivo será anexado à entrega)
- [ ] Cada integrante ensaiou **dois passos por slide** (não decorar: entender o movimento)