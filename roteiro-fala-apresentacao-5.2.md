# Roteiro de fala — Apresentação 5.2 (Mapeamento de Contextos)

---

## SLIDE 1 — Capa (A1 · 0:00–0:40)

**Na tela:** título + os 4 padrões (SK, C/S, P, C).

> Bom dia. O nosso tema é o de número 1.5: **Design Estratégico com Mapeamento de Relações entre Contextos** — Núcleo Compartilhado, Cliente-Fornecedor, Parceria e Conformista.
>
> Antes de começar, um parágrafo para amarrar o que veio antes. No tema da Linguagem Ubíqua, o grupo anterior mostrou que cada Bounded Context carrega o **próprio** significado — o "cliente" de vendas não é o "cliente" de cobrança. Só que o Evans, no livro de 2003, não para aí. Ele também responde à pergunta seguinte: **e quando esses contextos precisam conversar entre si?** Porque, na prática, nenhum sistema vive sozinho. É essa resposta que a gente apresenta hoje.
>
> A nossa base tem duas fontes: a palestra do Michael Plöd, da DDD Europe 2022, que o professor indicou; e o livro do Evans, que é a base de toda a disciplina.

*(Dica de cena: ao dizer os nomes dos 4 padrões, aponte para eles no slide, um a um, na ordem em que aparecem.)*

---

## SLIDE 2 — Roteiro (A1 · 0:40–1:00)

**Na tela:** 6 itens numerados.

> A gente vai seguir essa ordem: primeiro, o problema — como contextos isolados se integram; depois, as duas famílias de relação; em seguida, os **quatro padrões** do tema, cada um com definição, exemplo e custo; depois, um Context Map por inteiro; e, para fechar, como o mapa ajuda na prática, e as nossas conclusões.

*(CORTE POSSÍVEL: se o tempo apertar, este slide vira uma única frase — "seguimos do problema até os quatro padrões e as conclusões".)*

---

## SLIDE 3 — Do contexto isolado à integração (A1 · 1:00–3:00)

**Na tela:** bloco do recap (esquerda) + Lei de Conway (caixa cinza) + diagrama Vendas/Cobrança (direita).

> Recapitulando rápido o que já está estabelecido: cada contexto tem vocabulário próprio, e o Bounded Context é a **fronteira** dentro da qual aquele modelo e aquela linguagem valem. Fora da fronteira, a mesma palavra vale outra coisa.
>
> Só que sistemas reais **se integram**. O financeiro consulta o cadastro; a cobrança puxa dados de vendas. Aí aparece o problema que o tema de hoje resolve: **como juntar mundos diferentes sem que um contamine o modelo do outro?**
>
> O Plöd abre a palestra com uma frase do Robert Frost: *"boas cercas fazem bons vizinhos"*. As cercas são os Bounded Contexts — o tema 1.3 já mostrou isso. Mas cercas boas também precisam de **regras de convivência entre os vizinhos**. E essas regras são exatamente os padrões de relação do Context Map.
>
> E um fundamento aqui é importante — a **Lei de Conway**, que o Plöd cita: *"qualquer organização que projeta um sistema produz um design que copia a estrutura de comunicação da organização"*. E ele faz uma correção que muita gente erra: Conway não fala do **organograma** — aquela árvore estática. Fala da **comunicação real**: quem conversa com quem no dia a dia. Ele vai além e sugere até olhar a planta do andar — quais equipes dividem a mesma cozinha —, porque o que se conversa na cozinha também é comunicação.
>
> Então, as relações entre contextos não são só técnicas: são **organizacionais**. Cada seta entre dois contextos é, ao mesmo tempo, uma relação entre dois times.

*(No diagrama da direita: aponte "Vendas" e "Cobrança", leia as definições de cliente de cada um, e mostre a seta dupla — "hoje, essa seta é vaga: 'troca de informações'. Os padrões vão dar NOME e SEMÂNTICA a cada seta destsas".)*

---

## SLIDE 4 — As duas famílias (A1 · 3:00–5:00)

**Na tela:** duas caixas — simétricas × assimétricas.

> O Plöd classifica as relações em **duas famílias**, e essa divisão organiza tudo o que vem pela frente.
>
> Primeira família: relações **simétricas**. Nenhum lado comanda o outro — os dois dividem o mesmo destino, ou dividem um pedaço do modelo. São dois padrões: a **Parceria** e o **Núcleo Compartilhado**. Na notação, é a seta dupla: `A <-> B`.
>
> Segunda família: relações **assimétricas**, de *upstream* e *downstream* — a montante e a jusante. Um lado controla o modelo; o outro se adapta. Aqui entram o **Conformista** e o **Cliente-Fornecedor** — e, dentro delas, os papéis ACL, OHS e PL. Notação: seta simples, `A -> B`.
>
> Para fixar, a metáfora que o Plöd usa é a do **rio**. Quem está a montante joga uma cerveja no rio; quem está a jusante pega. E quem está a jusante **não consegue devolver** — nada sobe na contracorrente. Em software: o *upstream* muda o modelo e o *downstream* precisa se adaptar; o caminho inverso não existe. E o Plöd sublinha: isso é dinâmica de **poder** — o upstream detém o poder, e o downstream fica à mercê.

**[TROCA: A1 → A2]**

---

## SLIDE 5 — Parceria (A2 · 5:00–6:45)

**Na tela:** definição Evans (esquerda) + custo Plöd (direita) + notação embaixo.

> Começando pelos simétricos. **Parceria**: o Evans a define como a relação entre contextos cujo sucesso é **interdependente** — ou os dois dão certo juntos, ou os dois **falham juntos**. Não existe "metade entregue".
>
> Por isso, a definição do padrão exige **planejamento coordenado**: as duas equipes têm de gerir a integração e os lançamentos em conjunto. E vale observar: esse padrão **não aparece no código** — não tem classe, não tem interface. Ele é puramente organizacional.
>
> O custo real o Plöd revela com um exercício de plateia (34:30): ele desenha um time ao centro, conectado por parcerias a vários outros, e pergunta como é a vida desse time. A resposta que a sala escolheu — e que ele endossou — é: esse time **"vive em reuniões"** — coordenação atrai mais coordenação —, e o próprio trabalho dele fica para depois. Dá para operar assim; só que é a relação mais cara em comunicação.
>
> No exemplo que a gente vai ver adiante: `PolicyManagement <-> [P] RiskManagement` — o gerenciamento de apólices e o de risco, no mesmo sistema de seguros, que só funcionam juntos.

---

## SLIDE 6 — Núcleo Compartilhado (A2 · 6:45–8:45)

**Na tela:** diagrama Contexto A — [parte do modelo] — Contexto B, setas duplas.

> O segundo simétrico é o **Núcleo Compartilhado** — e a demonstração do Plöd é física (30:50): ele entrega uma barra com duas pontas, uma a cada lado da sala, e diz: *"quando eu puxo desse lado, você voa do outro"*.
>
> É isso o Shared Kernel: os dois contextos **compartilham uma parte do modelo** — tipicamente como um **artefato** concreto: uma biblioteca (jar, dll, módulo npm), um esquema de banco em comum, stored procedures. É o **acoplamento mais forte** que o DDD reconhece — mais forte até do que o do Conformista, que a gente vai ver agora: a parte compartilhada é **fisicamente a mesma coisa** dos dois lados; se muda de um lado, o outro **tem a obrigação** de ajustar junto.
>
> Quando evitar — segundo o Plöd e o Evans: **em microsserviços, sempre evitar** (quebra a independência de *deploy*, que é a razão de ser do microsserviço). E **entre times concorrentes, nunca** — o exemplo do Plöd: a montadora com dois fornecedores externos concorrentes; se os dois compartilham o núcleo, ele vira palco de jogo político.
>
> Quando o uso faz sentido, o Evans diz o que fazer: **minimizar** o que é compartilhado, **isolar** e **esconder** o núcleo — e nunca dar o controle dele a alguém de fora. E há uma exceção que o Plöd admite: quando **um mesmo time é dono** de dois contextos com vocabulário sobreposto — aí o Shared Kernel pode ser a escolha certa. A realidade vale mais que a pureza.

**[TROCA: A2 → A3]**

---

## SLIDE 7 — Conformista (A3 · 8:45–10:15)

**Na tela:** diagrama Upstream → Downstream ("adota o modelo").

> Passando ao lado assimétrico: o **Conformista** é o *downstream* que **adota o modelo do upstream** como se fosse dele — sem tradução, sem camada no meio. O Evans deixa claro que é uma **decisão explícita**: "nós seguimos a convenção do fornecedor".
>
> O Plöd resume o padrão assim: *"é uma escolha fácil — é rápida"*. Não se gasta nada com tradução; simplesmente se aceita o modelo de fora. **Mas** ele completa na sequência: o acoplamento vai **fundo, até o núcleo** da sua arquitetura. Quando o *upstream* muda o modelo dele, a mudança atravessa toda a sua aplicação — não para na borda.
>
> Quando é aceitável? O Plöd dá três heurísticas. Primeira: quando o modelo externo é **bom o suficiente** — bom e estável; um modelo próprio não agregaria nada. Segunda: para **economizar o esforço da tradução** — há situações em que o custo da camada não se paga. Terceira — e essa é curiosa —, o Conformista também pode ser uma decisão **política**: conceder o conformismo a um time é **reduzir o poder** dele; retirar, é devolver.
>
> O Evans ainda dá o guia prático: conforme-se a **modelos genéricos** — "pessoa", "endereço" —, porque o diferencial do negócio não está ali; o modelo próprio fica reservado ao seu núcleo.

---

## SLIDE 8 — Cliente-Fornecedor (A3 · 10:15–12:00)

**Na tela:** diagrama Fornecedor ↔ Cliente — duas setas: modelo (→) e voz no planejamento (←).

> O **Cliente-Fornecedor** é a relação assimétrica suavizada pela **negociação**. O Evans define: o fornecedor **respeita** as necessidades do cliente — e, principalmente, **abre espaço para elas no próprio planejamento**. É a única relação em que o *downstream* influencia o *roadmap* do *upstream*.
>
> O exemplo do Plöd usa dois times de banco: o time do **funil de crédito** mantém o formulário de empréstimo — é o *upstream*. O time de **scoring** avalia o risco com base naquele formulário — é o *downstream*. O scoring precisa de **dois campos novos** no formulário. Numa relação de montante e jusante pura, ele não teria voz alguma. No C/S, os dois negociam, e o acordo sai assim: *"te dou os dois campos — o resto do roadmap é meu"*. O fornecedor segue dono do seu conjunto, mas o cliente entra na pauta.
>
> O Plöd também batiza o **anti-padrão**: o *cliente impotente*. É o cliente que **não formula requisitos** nem participa — mas, quando o fornecedor precisa mudar, aparece com o **veto**: *"não tenho tempo; o risco é alto"*. Resultado: o fornecedor caminha sozinho, sem escutar o cliente, e o cliente fica à mercê. Pior dos dois mundos — e mais comum do que parece.

---

## SLIDE 9 — Os outros padrões (A3 · 12:00–13:00)

**Na tela:** lista de 4 padrões (ACL, OHS, PL, Separate Ways).

> Uma passada rápida nos outros padrões — o Context Map completo usa mais quatro além dos do tema.
>
> A **Camada Anticorrupção** é o contrário do Conformista: o *downstream* **traduz** o modelo do upstream para o próprio modelo. Custa o esforço da tradução, mas a mudança externa fica presa na borda. Aqui, o Plöd derruba um mito que vale registrar: *"a ACL não é desacoplamento — é acoplamento **solto**"*. A relação continua; o que a camada limita é o **alcance** do acoplamento.
>
> O **Serviço Aberto (Open Host Service)** é a API única que um contexto mantém para **muitos** consumidores ao mesmo tempo — o Google Maps é o exemplo clássico. Quem fornece um serviço aberto é quase sempre o *upstream*.
>
> A **Linguagem Publicada** é o vocabulário padrão, **publicado e acessível**, que os contextos assinam. O exemplo é o *iCalendar*: é por causa dele que Apple, Google e Microsoft evoluem os calendários **independentemente** — a conversa entre eles é um padrão, e não o modelo de ninguém.
>
> E **Caminhos Separados (Separate Ways)**: não integrar — por opção ou por custo. O exemplo do Plöd é o agente de call center com cinco telas abertas, copiando e colando à mão: é **integração organizacional**, feita por pessoas — e o mapa precisa registrá-la também.
>
> Com essas quatro, fecham-se os **nove padrões** de Evans e Vernon.

*(CORTE PARA 13 min: fale somente a ACL e o Serviço Aberto, uma linha cada, e a frase final da contagem.)*

---

## SLIDE 10 — Um Context Map por inteiro (A3 · 13:00–14:30)

**Na tela:** mapa Lakeside Mutual — 5 caixas azuis (os contextos) ligadas por 6 setas, cada uma com uma etiqueta branca de borda dourada ([OHS, PL], [CF], [ACL], [C]<-[S], [SK]<->[SK], [P]).

> Este é um Context Map **completo** — e ele é o momento em que a gente vê **todas as relações funcionando ao mesmo tempo**. Olhem primeiro para as **caixas**: cada caixa azul é um Bounded Context — o **Lakeside Mutual**, um sistema de seguros fictício, bem conhecido da comunidade DDD, tem cinco: o núcleo de cliente (**CustomerCore**), a administração de clientes (**CustomerMgmt**), o autoatendimento (**CustomerSelfService**), a gestão de apólices (**PolicyMgmt**) e a de risco (**RiskMgmt**).
>
> Agora as **setas** — seis relações. Vou percorrer uma a uma, e cada etiqueta é o padrão que a gente aprendeu:
>
> 1. **CustomerCore → CustomerMgmt, com [OHS, PL]**: o núcleo de cliente expõe um *Serviço Aberto* com *Linguagem Publicada* — ou seja: "meus dados de cliente estão disponíveis por essa API padrão, e é público".
> 2. **CustomerMgmt → CustomerSelfService, com [C] <- [S]**: o autoatendimento é o **Cliente** e a administração é o **Fornecedor** — a relação negociada: o autoatendimento pede ajustes, e o fornecedor abre espaço no planejamento.
> 3. **CustomerCore → CustomerSelfService, com [CF]**: o autoatendimento **adota o modelo** do núcleo de cliente — é o **Conformista**: sem tradução; o modelo de fora entra como se fosse dele.
> 4. **CustomerCore → PolicyMgmt, com [ACL]**: o gestão de apólices **protege** o próprio modelo com uma **Camada Anticorrupção** — o modelo do núcleo de cliente entra **traduzido**: o que vem de fora é convertido na linguagem interna.
> 5. **CustomerSelfService <-> PolicyMgmt, com [SK] <-> [SK]**: os dois **compartilham um pedaço do modelo** — é o **Núcleo Compartilhado**: um artefato pertence aos dois; mudou de um lado, o outro ajusta junto.
> 6. **PolicyMgmt <-> RiskMgmt, com [P]**: a gestão de apólices e a de risco têm sucesso **interdependente** — é a **Parceria**: ou os dois entregam juntos, ou falham juntos.
>
> Reparem no que este mapa faz: uma **única tela** responde — *quem fornece para quem, quem adota o modelo de quem, quem se protege com tradução, quem divide artefato, e quem depende do sucesso de quem*. Isso é a **visão sistêmica que o código não dá**: cada time, olhando o próprio repositório, enxerga só o seu pedaço; o mapa é o único desenho que junta tudo. Por isso ele é a ferramenta do **design estratégico**.
>
> E notem também a **relação com os times**: cada uma dessas setas é, ao mesmo tempo (Conway), uma relação entre duas equipes — o mapa desenha os dois mundos de uma vez: o técnico e o organizacional.

**[TROCA: A3 → A4]**

*(CORTE PARA 12 min: nos itens 1–6, percorre apenas os 4 do tema (2, 3, 4/CF, 5/SK, 6/P) e feche com a síntese — OHS/PL/ACL fique apenas citado.)*

---

## SLIDE 11 — Como o Context Map ajuda na prática (A4 · 14:30–15:30)

**Na tela:** "Para a equipe e o projeto" (esquerda) + "O caso do veto — Plöd 52:00" (direita).

> Para que serve o Context Map **na prática**? Três respostas.
>
> Primeira: **visão do sistema inteiro** — o que acabei de mostrar: cada time enxerga só o seu repositório; o mapa junta tudo.
>
> Segunda: **revela a comunicação real** entre os times — a comunicação de que fala a Lei de Conway —, inclusive a que ninguém documenta: quem fala com quem, quem depende de quem, e onde o fluxo de influência está travado.
>
> Terceira: **expõe dependências e riscos escondidos** em cada integração — o Shared Kernel que ninguém admite, o conformismo que ninguém percebeu que assumiu, a tradução que ninguém mantém.
>
> E a prova de que o mapa revela o que ninguém quer confessar é a história que o Plöd conta (52:00): em uma empresa, um gerente **vetava toda mudança numa API** — e o motivo não era técnico: ele estava **travando os times rivais** — times dependiam das modificações para evoluir seus produtos, e o veto os **bloqueava** — na disputa de uma promoção. Quem descobriu o jogo foi a equipe que **desenhou o Context Map**: ao desenhar a dependência e a dinâmica de poder, o veto ficou visível.
>
> O Context Map é, antes de tudo, uma **ferramenta de análise**: antes de codificar, ele torna a integração **discutível**.

---

## SLIDE 12 — Conclusões (A4 · 15:30–17:30)

**Na tela:** 5 mensagens com travessão.

> Fechando, cinco conclusões.
>
> **Primeiro **— talvez a principal: as relações entre contextos têm **semântica de poder**. Uma seta entre dois contextos jamais é só "o sistema A chama o B". Ela diz quem controla o modelo, quem se adapta a quem, e quem entra no planejamento de quem.
>
> **Segundo**: escolher o padrão é, antes de tudo, uma decisão de **acoplamento** — o grupo organizou num espectro: o **Núcleo Compartilhado é o mais forte**, físico; o **Conformista** é profundo, mas sem o compartilhamento do artefato; o **Cliente-Fornecedor** negocia o acoplamento; e a **Camada Anticorrupção** e os padrões de papéis são os mais soltos — limitados à borda.
>
> **Terceiro, ** duas lições do Plöd que ficam: a ACL **não é desacoplamento** — é acoplamento solto; e um **núcleo de domínio** jamais deveria se conformar a um sistema externo — porque o núcleo é o diferencial do negócio, e depender lá da agenda de um fornecedor é o pior cenário possível.
>
> **Quarto**: o Context Map **revela a comunicação real** — a de Conway —, inclusive o que ninguém documenta: caso do veto, que expõe política organizacional.
>
> **E quinto**, amarrando com a disciplina: a **Linguagem Ubíqua definiu o vocabulário dentro** de cada cerca. O **Context Map é a linguagem entre as cercas** — a linguagem ubíqua "de segunda ordem": o vocabulário dos padrões com o qual desenhamos e negociamos as fronteiras. A sequência de temas da disciplina forma este arco: contexto, linguagem — e agora **relação**.

*(CORTE PARA 12 min: a Quarta (caso do veto) é o corte de emergência — mas é o melhor gancho de perguntas; corte por último.)*

---

## SLIDE 13 — Referências (A4 · 17:30–17:50 + perguntas)

**Na tela:** 4 referências.

> As nossas fontes estão na tela: o livro do Evans — a base da disciplina; a palestra do Plöd, que o professor indicou; o material do DDD Crew, que a gente usa agora no questionário; e a leitura de Team Topologies sobre interação entre times, que o Plöd referencia. Obrigado — e ficamos à disposição para as perguntas.

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
| 7 | Conformista | A3 | Padrão C | 1:30 | 1:30 |
| 8 | Cliente-Fornecedor | A3 | Padrão C/S | 1:45 | 1:45 |
| 9 | Outros padrões | A3 | Visão geral | 1:00 | **0:30** (corte) |
| 10 | Context Map completo | A3 | Síntese visual | 1:30 | **1:00** (corte) |
| 11 | Mapa na prática | A4 | Aplicação | 1:00 | 1:00 |
| 12 | Conclusões | A4 | Síntese | 2:00 | **1:30** (corte) |
| 13 | Referências | A4 | Encerramento | 0:20 | 0:20 |
| | | | **Total** | **~17:10** | **~12:00–13:30** |

## Checklist antes de apresentar

- [ ] Nomes na capa (substituir `[NOMES DO GRUPO]`)
- [ ] Artigo validado com o professor no Teams **antes da data limite** (a apresentação pode não citar o artigo, mas a validação é exigida pelo guia)
- [ ] Questionário (5 perguntas, Wayground) pronto e **não divulgado** a ninguém fora do grupo
- [ ] Link de edição do quiz enviado ao professor com antecedência
- [ ] Ensaio cronometrado pelo menos uma vez com o grupo inteiro
- [ ] Cada integrante ensaiou **dois passos por slide** (não decorar: entender o movimento)
- [ ] Exportar em PDF como backup (o arquivo será anexado à entrega)
