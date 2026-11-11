# Tradução do Artigo (PT-BR)

**Original:** ÖZKAN, Ozan; BABUR, Önder; VAN DEN BRAND, Mark. **"Refactoring with domain-driven design in an industrial context: an action research report"** · *Empirical Software Engineering* (Springer), 28:94, 2023 · DOI: [10.1007/s10664-023-10310-1](https://doi.org/10.1007/s10664-023-10310-1)
**Acesso:** aberto (Springer). Afilições: Universidade Técnica de Eindhoven (TU/e) e Wageningen University & Research (WUR), Países Baixos.
**Comunicado por:** Daniel Méndez. **Palavras-chave:** domain-driven design · action research · software refactoring · software architecture · microservices.
**Nota:** termos técnicos mantidos em *itálico* na 1ª ocorrência; N.T. = notas do tradutor. Tradução de apoio para o grupo — citações na apresentação devem remeter ao original.

---

## Resumo (tradução)

**Contexto** — Desenvolvedores de software precisam evoluir constantemente a estrutura e a estabilidade do código devido às necessidades de negócio em mudança do produto. Há diversas abordagens de refatoração na indústria que prometem melhorias na composição do código e na manutenibilidade.

**Objetivo** — Queremos melhorar a manutenibilidade de um sistema existente por meio da refatoração usando o *Domain-Driven Design* (DDD) como abordagem de projeto. Também buscamos fornecer evidência empírica de seu efeito sobre a manutenibilidade e dos desafios percebidos pelos desenvolvedores.

**Método** — Aplicamos a metodologia **pesquisa-ação**, que facilita a colaboração próxima academia-indústria e a presença regular no produto estudado. Utilizamos *focus groups* para descobrir os problemas do sistema existente com abordagem qualitativa. Revisamos a base de código para construir nossa própria opinião de especialistas e identificamos problemas no código, correlacionando-os aos apontados pelos engenheiros do time. Refatoramos o sistema existente de acordo com os princípios de DDD. Para medir os efeitos, utilizamos o questionário **mTAM** (*mini Technology Acceptance Model*), entrevistas semi-estruturadas com o time e *card sorting* para a análise qualitativa. Para reduzir viés, complementamos a medição com **três engenheiros recém-chegados** através do protocolo *think-aloud*.

**Resultados** — Identificamos que os engenheiros deram respostas majoritariamente **positivas** às perguntas, mapeadas para as métricas de manutenibilidade da ISO/IEC 25010. Nossa refatoração DDD obteve **85 em Utilidade Percebida (PU)** e **83 em Facilidade de Uso Percebida (PEU)**, resultando em **score geral mTAM de 84 de 100**, que mapeia um **bom** resultado geral em termos do modelo de aceitação e classificação média conforme a literatura.

---

## 1. Introdução

Sistemas de software devem mudar constantemente ao longo do tempo para implementar requisitos funcionais e não-funcionais novos. Com isso, o tamanho e a complexidade do sistema aumentam continuamente, o que eventualmente degrada a qualidade do software (Lehman 1980). Para manter o nível de qualidade, o sistema deve ser mantido e adaptado com rigor. Este é um desafio contínuo e vital para desenvolvedores e empresas — a literatura estima que a manutenção de software representa **até 70–80% dos custos de desenvolvimento** (Schach 2011).

A **refatoração** é uma das principais atividades de manutenção para garantir a qualidade: é o processo de alterar um sistema de software de modo que **não altere o comportamento externo do código e, no entanto, melhore sua estrutura interna** (Fowler 1999). Como Mens e Tourwé (2004) observam, é um processo tangível, que resolve problemas conhecidos mas ao mesmo tempo tem efeitos colaterais significativos — mudanças de padrões de projeto, responsabilidades de componentes e complexidade. Esses efeitos podem criar novos desafios na introdução de *features* futuras, e podem introduzir dívida técnica (*tech debt*), como bugs, exigindo um grande número de transformações de código. Logo, a refatoração deve ser bem-projetada e executada de forma disciplinada (Abid et al. 2020).

Diversas abordagens existem na literatura e na indústria para planejar e executar refatorações (Abid et al. 2020), com múltiplas reivindicações sobre os tipos de problema resolvidos e a efetividade na prática. Um exemplo é **utilizar o DDD como abordagem de refatoração sistemática**. Nossa hipótese é que o DDD tem histórico comprovado como boa ferramenta de refatoração em sistemas como o produto estudado (Evans 2003; Fowler 2020, 2003; Oukes et al. 2021; Wade e Salahat 2009; Braun et al. 2021; Kapferer e Zimmermann 2020; Landre et al. 2007).

Neste artigo, abordamos um caso de refatoração **em ambiente industrial**, para melhorar a manutenibilidade de um software **com DDD**. A pesquisa foi executada num produto lançado e usado diariamente por clientes; os autores estiveram **imersos na indústria**, justificando decisões de projeto e avaliando metodologicamente a efetividade da refatoração DDD. Adotamos a metodologia **pesquisa-ação** (*action research*) (Staron 2020) porque ela investiga **como uma intervenção afeta um contexto real**.

Nossa contribuição: (1) identificamos um problema de manutenibilidade no parceiro industrial; (2) propusemos um plano de solução via refatoração com DDD; (3) implementamos a solução **no contexto real**; e (4) avaliamos a **efetividade e utilidade percebidas** pelas partes interessadas. Focamos no percebido, pois o problema é **socio-técnico** (Mens 2016). Assim, buscamos respostas empíricas a três perguntas de pesquisa (RQ) em contexto industrial:

- **RQ1:** Como podemos melhorar a manutenibilidade do sistema de software atual?
- **RQ2.1:** Como a refatoração baseada em DDD afeta a manutenibilidade do sistema, **na percepção dos desenvolvedores**?
- **RQ2.2:** Quais são os **desafios** de refatorar usando DDD?

A RQ1 busca entender quais ações aumentar a manutenibilidade do sistema atual e seus efeitos — especialmente num código-base de um produto que clientes usam de fato. A RQ2.1 busca entender o papel do DDD nos esforços de refatoração. Como o DDD é uma abordagem **opinionada** (com forte direcionamento), também queremos saber os desafios de implementá-la num código-base existente (RQ2.2): funciona "como está", ou os desenvolvedores precisam de abordagens específicas? Funciona em cooperação com tecnologias modernas?

O restante do artigo: Seção 2 resume os antecedentes (DDD e pesquisa-ação); a Seção 3 o desenho de pesquisa; a Seção 4 a seleção do produto; a Seção 5 os problemas identificados; a Seção 6 a refatoração; a Seção 7 resultados; Seção 8 lições; Seção 9 ameaças; Seção 10 conclusão.

---

## 2. Fundamentação

### 2.1 Essenciais do DDD

O **DDD** é uma abordagem de desenvolvimento na qual **a estrutura do código-fonte — nomes de classes, métodos e variáveis — deve corresponder ao domínio de negócio**. Surgiu como solução poderosa para demandas complexas de negócio e abstração efetiva no projeto e implementação de software. Foi introduzida por **Eric Evans** em seu livro (Evans 2003) como extensão do conceito de domínio. Fowler define o DDD como a abordagem que **centra o desenvolvimento na programação de um modelo de domínio** que tenha compreensão rica dos processos e regras do domínio (Fowler 2020).

O **domínio**, no contexto de engenharia de software, refere-se à área de conhecimento em que o software operará. Evans simplifica: *"é a coisa sobre a qual o software é feito"*. O domínio é às vezes chamado *domínio do problema*. Exemplo: um software para gerir a cadeia de suprimentos de um fabricante de automóveis — todas as técnicas, regras, especificações e preocupações necessárias para gerir essa cadeia de suprimentos (o **conhecimento**) constituem o domínio. Nesse nível, o domínio é apenas uma esfera de conhecimento, uma definição de terminologia, problema e complexidade — **não uma implementação** (Evans 2003). Na fase de projeto, todo o conhecimento e a terminologia do domínio são aplicados à arquitetura e funcionalidade do software. O domínio é a área de expertise **abstraída dos detalhes de implementação**.

O DDD amplia o conceito de domínio (Evans 2003): seu objetivo é **criar e manter aplicações complexas de forma mais fácil por meio de um modelo em evolução**. Com o DDD, o projeto de software torna-se uma descrição mais adequada de como o software funciona em alto nível (Fowler 2003). O DDD baseia-se em **três princípios fundamentais**:

1. Colocar o foco principal da aplicação no **domínio central e na lógica do domínio**;
2. Basear projetos complexos **num modelo do domínio**;
3. **Colaborar continuamente com especialistas do domínio** para melhorar o modelo e resolver questões do domínio.

Esses princípios potencialmente alteram as práticas comuns dos processos convencionais de projeto de software, onde o foco primário é a arquitetura de software e detalhes de implementação.

*(N.T.: a Seção 2.1 do original continua descrevendo os benefícios do DDD — alinhamento código-negócio, linguagem ubíqua e a divisão estratégico/tático; os trechos completos estão no PDF, págs. 4–6.)*

### 2.2 Pesquisa-ação (Action Research)

A **pesquisa-ação** é uma metodologia de pesquisa em que o pesquisador **intervém no contexto real** e observa os efeitos da intervenção — diferindo de métodos observacionais ou experimentais. É caracterizada por **colaboração estreita** com o contexto de estudo e **iteração entre diagnóstico, planejamento, ação e avaliação** (Staron 2020). É apropriada quando o estudo é socio-técnico e envolve pessoas de verdade trabalhando num produto real.

---

## 3. Desenho de Pesquisa

Os autores descrevem o desenho da pesquisa-ação: participação direta, coleção e análise multimétodo, e o compromisso de proteger a propriedade intelectual da empresa participante (nomes reais de componentes redigidos, arquitetura real não publicada).

### 3.2 Produto estudado

O produto estudado é um produto **industrial primário** que gere o **ODD (Operational Design Domain) de veículos autônomos**, permitindo às montadoras decidir **onde é seguro para os motoristas ativarem as funções de condução automatizada** dos veículos. Tem um editor *web* intuitivo em que a montadora cria **regras e restrições de direção autônoma**; além de um serviço em nuvem para processar as atualizações e enviá-las diretamente aos veículos. As atualizações são entregues **over-the-air** por um produto de entrega crítico de segurança, desenvolvido por outro time da mesma organização. O produto já foi lançado às montadoras e é continuamente melhorado. Tem componentes de *frontend*, *backend*, bancos de dados, testes e infraestrutura como código — todos implementados pelo mesmo time de produto. O *frontend* é **TypeScript com AngularJS**; comunica-se com o *backend* por **endpoints REST**. O *backend* é **Java com Spring Framework** e implementa toda a lógica de negócio e de domínio; conversa com serviços de terceiros e bancos como **PostgreSQL**. Tudo é implantado na **Azure** (nuvem).

### 3.3 Time do produto

O time tem **13 desenvolvedores full-time diversos**: Gerente de Produto, Arquiteto do Sistema, Designer UX, Líder de Testes e Engenheiros de Software. Trabalham em **Agile com sprints de 2 semanas** e princípios EPT, com pipelines de **integração contínua**, processos de gestão de requisitos e de **conformidade de segurança**. Os engenheiros têm níveis variados de experiência tanto na indústria quanto **no DDD**.

### 3.4 Time da pesquisa-ação

Três pesquisadores: dois docentes como conselheiros e um doutorando que executa a pesquisa **no produto**, sendo também **engenheiro sênior do produto** na mesma empresa, trabalhando full-time nele.

### 3.5 Coleta e análise de dados

Vários métodos: (i) **descoberta de problemas** via ***focus group*** (mini-*focus group*, com as normas de Kontio et al. 2004) — motivado por: (1) o time já tinha mais de 10 reuniões de grupo para identificar e discutir problemas técnicos, (2) desejavam ambiente de discussão com especialistas para obter julgamento especializado, (3) era rápido e barato pelo pequeno número de especialistas; (ii) **entrevistas semi-estruturadas**; (iii) questionário **mTAM** — com **6 perguntas de Utilidade Percebida (PU)** e **6 de Facilidade de Uso Percebida (PEU)**, escala Likert 1–7, mais 1 pergunta de recomendação (escala 1–10); o mTAM é desenhado de modo similar ao SUS (*System Usability Scale*); (iv) ***think-aloud*** com engenheiros novos; e (v) ***card sorting*** para a análise qualitativa. A *manutenibilidade* é avaliada segundo as dimensões da **ISO/IEC 25010**. Para minimizar viés de quem participou da refatoração, 3 **engenheiros novos** no time foram incluídos com o protocolo *think-aloud*.

### 3.6–3.7 Ética e disponibilidade de dados

O estudo envolve participação humana, com os devidos cuidados éticos; os *datasets* gerados foram disponibilizados ao acesso público (com a devida restrição de propriedade intelectual da empresa).

---

## 5. Problemas Identificados

Identificamos os seguintes problemas com base nas entrevistas de *focus group* com **7 engenheiros de software** que trabalham diariamente no sistema. Pedimos que o grupo apontasse os problemas no desenvolvimento, as causas e como resolvê-los. A análise de atributos (Tabela 2 do original) resumiu:

| Atributo | Ocorrências |
|---|---|
| Problema: duplicação de código (sobretudo em *services*) | 6 |
| Problema: manutenibilidade de código | 5 |
| Problema: objetos de domínio sem lógica | 4 |
| Problema: manutenibilidade de testes | 4 |
| Solução: refatorar código | 4 |
| Solução: ferramentas e *frameworks* melhores | 4 |
| Solução: melhorar qualidade de código | 3 |
| Solução: melhores padrões de objetos de domínio | 3 |

Correlacionamos os resultados do *focus group* à opinião de especialistas dos autores, via revisões de arquitetura e de código. Conclusão: **problemas arquiteturais**. O sistema contém o **anti-padrão Anaemic Domain Model** — em oposição aos princípios de orientação a objetos (Fowler 2003) — e a lógica de negócio **duplicada em vários serviços**, **não encapsulada**. O sistema também implementa um **repositório centralizado** na camada de acesso a dados — uma *god class* de todo o acesso ao banco — e as dependências *Domain Object*–*DTO* não seguem um padrão.

### 5.1.1 Anaemic Domain Model

O projeto do *backend* pode ser descrito como um **Anaemic Domain Model**: objetos de domínio contêm **pouca ou nenhuma** lógica de negócio. Martin Fowler, que descreveu o padrão, o considera um **anti-padrão**: *"o horror fundamental desse anti-padrão é que ele é tão contrário à ideia básica do projeto orientado a objetos, que é combinar dados e processá-los juntos"* (Fowler 2003). Segundo Fowler, é prática comum em aplicações de serviços Java e .NET de três camadas — especialmente as que usam tecnologias como *Entity Beans*; no nosso caso, pode ser considerado o **Spring Framework**. Ao avaliar o *backend* atual, vemos **fortes indícios do Anaemic Domain Model**: validações, cálculos, **regras de negócio** e a lógica central de negócio são sempre implementados **nas camadas**, quando necessários para um caso de uso particular. Os objetos que representam os *business objects* — que podem ser considerados objetos de domínio — são **objetos de valor sem validação, cálculo ou regras de negócio**, apenas carregando dados. Essa situação potencialmente produz **objetos de domínio sem checagem** e lógica central de negócio comprometida: a validade desses objetos e da lógica central é potencialmente comprometida. Embora haja testes unitários, de integração e de integração de sistema checando a validade da informação gerada e da lógica de negócio, dado que o produto estudado é **crítico para a segurança** (*safety-critical*), resta um risco substancial.

### 5.2 Problemas operacionais

Os problemas arquiteturais geram problemas operacionais: testes e código **difíceis de manter**.

**5.2.1 Testes são difíceis de manter** — Revisamos a implementação de testes contra o conceito de *test smells* (Van Deursen et al. 2001). Os efeitos do *Anaemic Domain Model* e da lógica de negócio distribuída também se veem nos testes: os testes unitários e de integração de sistema do produto contêm **7 dos 11 **test smells*** definidos (Mystery Guest, Resource Optimism, General Fixture, Eager Test, Lazy Test, Indirect Testing, Test Code Duplication). O código de teste é também difícil de manter por causa de *mocks* e *asserts* longos e complexos sobre estados, objetos e métodos esperados. A integridade dos objetos de domínio usados no negócio sob teste é verificada a cada teste, já que os objetos de domínio **não implementam lógica de negócio testável nem restrições**. Com uma adição ou modificação num caso de negócio, **todos os testes relacionados** precisam ser modificados/adaptados à nova implementação. O *backend* atualmente tem **cerca de 1.200 cenários de teste unitário** em que a maior parte da lógica de negócio é **desnecessariamente testada repetidamente**, mas a essência de cada teste unitário deveria ser testar a validade de um certo caso de uso de negócio — que também teve de implementar lógica de negócio, porque a lógica central **não é encapsulada nem testada uma única vez**.

**5.2.2 O código é difícil de manter** — Um dos problemas que o time de desenvolvimento sofre e reconhece é a manutenibilidade do código-base. Não é surpresa, dada as questões anteriores: cada uma contribui para o código-base difícil de manter. O time afirma que a maior parte do tempo **tem dificuldade de implementar algo compatível com o código-base atual**, precisando retrabalhar ou refatorar o que implementou antes de implementar novos requisitos. Também disse que implementar *features* em cima de negócios anteriormente implementados **é difícil** a lógica de ser seguida.

---

## 6. Sistema Refatorado

A refatoração seguiu os princípios do DDD. As responsabilidades de controllers, services, *domain objects* e *repositories* foram redesenhadas segundo a **Linguagem Ubíqua** e os padrões do Evans.

**6.2 Controllers** — Redefinimos o escopo: *controllers* **finos** e focados em ações, seguindo o **Princípio de Responsabilidade Única**; removemos toda a lógica de caso de uso e de domínio. Sua responsabilidade agora: expor *endpoints* REST, atuar como interface da aplicação, fazer **validações conforme a especificação** da API e **despachar** requisições ao *Application Service* ou *Domain Service* relacionados. Resultado: **menor superfície de mudança**, *controllers* mais adaptativos, fáceis de testar e manter.

**6.3 Services** — Separámos o conhecimento de **caso de uso de negócio** do conhecimento **de domínio**, em serviços distintos.

**6.3.1 Application Service** — Introduzimos o conceito de *Application Service* para **encapsular e implementar casos de uso de negócio específicos dos *endpoints* REST**, quando necessário. Implementa a lógica requerida pelo caso de uso **agregando vários serviços da camada de Serviços de Domínio**; também executa as conversões do objeto de domínio fornecido pelo serviço de domínio para o **Data Transfer Object** requerido pelo *controller*, conforme a especificação da API.

**6.3.2 Domain Service** — Evans pensa que o *service* é uma camada *stateless* usada quando há um processo ou transformação significativa no domínio **cuja responsabilidade natural não é de nenhum objeto de domínio ou objeto de valor** (Evans 2003). Seguindo a descrição, definimos os *domain services* como lugares que detêm uma certa parte do **conhecimento do domínio**, implementam lógica requerida pelo domínio mas **não** responsabilidade de um único objeto — podem agregar vários objetos de domínio/objetos de valor, ou orquestrar/computar uma certa lógica que envolve *repositories* ou dependências externas. Nossa implementação de *domain services* não é muito diferente de um serviço em microsserviços; contudo, são **auto-contidos** e responsáveis por apenas **uma certa lógica de domínio**.

**6.4 Repositories** — Evans sugere o *Repository Pattern* para **encapsular o acesso a dados** e aproveitar melhor o foco dirigido a modelo (Evans 2003). No conceito original, *repositories* são extensões dos *Domain Objects*, acrescentando a capacidade de comunicar com a fonte de dados diretamente. No nosso *backend*, a comunicação com a fonte já estava encapsulada na camada de *Repository* e sem dependência dura dos objetos de domínio — mantivemos a abordagem para compatibilidade com a arquitetura e os frameworks, mas **redesenhamos o projeto e as responsabilidades dos *repositories* com abordagem mais dirigida ao domínio**, introduzindo implementação de repositório **específica por recurso**.

**6.5 Domain Objects** — A terminologia de DDD de Evans descreve *domain objects* como objetos da área específica de negócio que representam algo **significativo para o especialista do domínio** — majoritamente **entidades e objetos de valor**. No nosso caso, o *backend* já definia objetos imutáveis para capturar informações de domínio; contudo, **redesenhámos os objetos de domínio segundo a Linguagem Ubíqua** e **adicionámos mais responsabilidades**: almejamos capturar melhor as informações e **restrições** do domínio e encapsulá-las, para ter uma **fonte única de verdade**. Para conseguir isso, **estendemos os objetos com o conhecimento das restrições e validações** do domínio de negócio, e **encapsulamos transições de estado e cálculos do domínio** dentro dos objetos. Com isso, introduzimos uma **fonte única confiável** da representação do domínio de negócio em todo o código do *backend*.

**6.6 Data Transfer Objects** — Estendemos a responsabilidade dos DTOs **movendo as validações de restrição e as conversões dos *controllers* para os DTOs**. Assim, os DTOs ficaram **mais inteligentes**, aderentes aos princípios **SOLID** e com comportamento fortemente testado. Os *controllers* também se beneficiam pois os DTOs capturam os parâmetros e restrições especificados pela API do *backend*. Como os DTOs implementam validações e conversões próprias para entrada e saída, **encolhemos ainda mais a superfície de implementação dos *controllers***.

**6.7 Bounded Context** — O *bounded context* é um **padrão central do DDD** (Evans 2003): uma **área delimitada** na qual um modelo particular de domínio **aplica**. Na nossa refatoração, implementamos **um *bounded context* para cada um dos nossos serviços de domínio** (Seção 6.3.2). Não podemos revelar a arquitetura real, mas, como exemplo, podemos falar de um **Car Service** e um **Driving Rule Service** imaginários. Cada um desses serviços tem o **seu banco, controller e REST API** — o que ajuda a **isolar os dados e as operações** dentro do *bounded context* do serviço: cada serviço **evolui e é modificado de forma independente**, sem afetar o sistema como um todo. Além desses *bounded contexts* individuais, também temos os **Application Services** (Seção 6.3.1), que **agregam dados de múltiplos *bounded contexts***. Por exemplo, um *Car Rules Application Service* que usa ambos o Car Service e o Driving Rule Service. Na Fig. 5 do original, a arquitetura *backend* pós-refatoração é mostrada com **classes, relacionamentos e o *Bounded Context* com códigos de cores**: o *Bounded Context* marcado em **verde é o Car Context** e **em azul o Driving Rules Context**. Os nomes de classes, variáveis e métodos são **exemplos** e não refletem o código real, por restrição de propriedade intelectual.

**6.8 Intention-Revealing Interfaces** — No livro, Evans (2003) sugere usar *Intention-Revealing Interfaces* para **capturar lógica de domínio significativa no código**, tornar o efeito do código claramente compreensível ao usuário e antecipar o efeito de uma mudança enquanto consome a implementação. Para garantir que o código seja facilmente compreensível e mantível, **nomeámos os métodos do *backend* da mesma forma que as operações de domínio definidas pela nossa Linguagem Ubíqua**.

**6.9 Testes** — Como parte da refatoração, os testes foram também redesenhados: reduzindo *mocks* e duplicações, com testes de caso de negócio por cenário.

*(N.T.: os detalhes das subseções 6.1, 6.4 final, 6.6 exemplos e 6.9 estão no PDF original, págs. 19–24.)*

---

## 7. Resultados e Avaliação

Nesta seção, reportamos os resultados das mudanças de refatoração com base no questionário, nas entrevistas e nos dados do *think-aloud*, na ordem das perguntas de pesquisa. As informações das seções anteriores respondem à **RQ1** (como os problemas foram identificados, por que o DDD foi o método da refatoração, e como a solução foi implementada no sistema).

### RQ2.1 — Efeito da refatoração DDD na manutenibilidade, na percepção dos desenvolvedores

Para responder à RQ2.1, interpretamos **entrevistas**, **mTAM** e ***think-aloud***. Como enfatizamos a manutenibilidade do sistema, a estrutura do reporte segue as **métricas da ISO/IEC 25010** (Seção 3.5.3).

**Compreensibilidade** — Segundo os participantes, o código refatorado é **mais compreensível** na majorityia dos casos, **por sua semântica e arquitetura orientada ao negócio**: os participantes disseram conseguir seguir com facilidade a lógica e as conexões entre classes e métodos, porque **o caso de negócio implementado é mais refletido no código** — na arquitetura, nas responsabilidades das classes e na escolha de nomes de métodos e variáveis. A **encapsulação** e a **reusabilidade** do código pós-refatoração também permitem seguir o código com mais facilidade, pois são implementadas **no escopo respectivo, uma vez só**, padronizadas em todo o código-base. Quanto aos testes, os *statements* também foram bem pontuados — **os testes depois da refatoração DDD são mais fáceis de entender**. Um dos participantes: *"o código na verdade consiste de ações de cenário, **ele fala por si mesmo** (he speaks for itself). Uma vez que você conhece o cenário de negócio, entender o código é muito mais fácil. A divisão lógica da implementação também ajuda muito a entender o que está acontecendo."*

**Modularidade** — **Quatro dos cinco participantes foram muito positivos**. Combinavam frequentemente os desafios que tinham com o código anterior — quando precisavam modificar alguma parte da lógica de negócio implementada — comparando-o com o código refatorado, para reconhecer e apreciar as melhorias. Segundo suas respostas, um **pequeno** caso de negócio no nível do produto **exigia uma pegada de mudança muito grande**, porque o acoplamento era grande e monolítico; pós-refatoração, a mesma mudança fica **localizada**.

**Modificabilidade e testabilidade** — Os engenheiros apontaram **menos *mocks* e menos refatoração** ao manter o código, **menos duplicação**, e **criar/manter testes é mais fácil** — testes por **cenário**, não por detalhe interno, com a integridade dos objetos de domínio garantida **pelos próprios objetos** (validações dentro).

### Tabela 7 do original (tradução) — mTAM por pergunta (Likert 1–7; Q13 de 1–10)

| # | Pergunta | Resultado |
|---|---|---|
| **Utilidade Percebida (PU)** | | |
| 1 | Usar DDD me permite concluir tarefas de desenvolvimento **mais rapidamente** | **6** |
| 2 | Usar DDD **melhora meu desempenho** no trabalho | **6** |
| 3 | Usar DDD durante o desenvolvimento **aumenta minha produtividade** | **6** |
| 4 | Usar DDD **potencializa minha efetividade** nas tarefas de implementação | **6** |
| 5 | Usar DDD **facilita** a implementação | **6,25** |
| 6 | Achei o DDD **útil** na implementação | **6,25** |
| **Facilidade de Uso Percebida (PEU)** | | |
| 7 | **Aprender** a implementar com DDD foi fácil para mim | **5,75** |
| 8 | Achei fácil **fazer o DDD fazer o que eu quero** | **6** |
| 9 | Minha interação com o DDD tem sido **clara e compreensível** | **6** |
| 10 | Achei o DDD **flexível** de interagir | **5,5** |
| 11 | Foi fácil ficar **habilidoso** no uso do DDD | **6** |
| 12 | Achei o DDD **fácil de usar** | **5,75** |
| **Encerramento** | | |
| 13 | **Recomendaria o DDD a outros?** (1–10) | **8,5** |

Com a curva da SUS (Bangor et al. 2009; Fig. 6 do original), um score **84/100** se posiciona na faixa de avaliação **"boa"** — os engenheiros **reconhecem os ganhos positivos da refatoração DDD e a acham útil de forma geral**. O questionário mTAM mostra que os engenheiros **percebem o DDD como uma abordagem que os permite concluir tarefas de desenvolvimento mais rapidamente, aumenta a produtividade e potencializa a efetividade nas tarefas de implementação**.

### RQ2.2 — Desafios da refatoração com DDD

Durante o estudo, encontramos **vários desafios**, relacionados (i) à **adoção e compreensão dos princípios de DDD** pelos engenheiros e (ii) aos **desafios técnicos** de usar o DDD em cooperação com **frameworks opinionados** já presentes no código (Dinh-Tuan et al. 2020).

**Onboarding de engenheiros ao DDD não é fácil** — Embora os participantes sejam positivos quanto à refatoração DDD, o aspecto mais citado foi que **o DDD introduz muito encapsulamento e muitos níveis de abstração**. Os participantes afirmaram que é **desafiador para os desenvolvedores sem experiência prévia em DDD** entender a dependência entre classes, métodos e **como certa lógica de negócio está dividida**; sobretudo no início, tiveram desafios para compreender **por onde começar** a implementar a solução que tinham em mente. Esse fato também se vê na Tabela 5 do original: os *statements* negativos se concentram em **experiência, abstração e compreensibilidade**. As respostas se consolidam: engenheiros **sem experiência prévia** têm dificuldades no *onboarding*, mas **após algum tempo passam a ver melhorias inegáveis**; os com **experiência prévia** não encontram dificuldades no *onboarding* e captam a ideia mais rápido. Os que tiveram dificuldades superaram treinando-se com **materiais online e estudando a implementação de exemplo** introduzida como parte deste estudo.

**Refatorar num código-base em fase de desenvolvimento é desafiador** — Executamos o estudo num produto **em fase de desenvolvimento**. Por novos requisitos e metas de negócio, o time de desenvolvimento **adicionava features constantemente** e mudava a maioria da lógica de negócio com frequência — o que afetava de tempos em tempos os nossos esforços de refatoração. Nossa solução foi executar a refatoração **num ambiente isolado** — o que também é sugerido pelo Evans — e então trabalhar a **paridade de features** antes de deprecar a implementação antiga e adotar a refatorada.

**Implementar o DDD exatamente como descrito nas diretrizes nem sempre é possível com frameworks modernos** — Desde o livro de Evans, houve muitas melhorias nas linguagens com a introdução de frameworks modernos. O produto estava usando **Spring Boot**, **Lombok**, **jOOQ**. Alguns são muito *opinionated* — criam suas abstrações e até **injetam sua DSL** no código. Por seus requisitos arquiteturais e de estilo de codificação, às vezes **não era totalmente possível implementar o DDD como descrito no livro**. Evans também reconhece isso: *"Em geral, **não brigue com seus frameworks**. Procure manter os fundamentos do design dirigido a domínio e deixe de lado os detalhes quando o framework é antagonista"* (Evans 2003). Neste estudo, aplicamos a mesma mentalidade e **não brigamos com os frameworks**: usamos os frameworks para implementar **os fundamentos** do DDD do modo que eles permitiam.

---

## 8. Lições Aprendidas

Nossos achados mostram que **usar uma abordagem de projeto opinionada como o DDD é uma boa ferramenta** para resolver problemas comuns de desenvolvimento de software e **traz padronização ao código-fonte**. Essa padronização oferece **estrutura limpa** — e **orienta** os engenheiros que desenvolvem o produto, seja ao projetar a solução de uma *feature* nova, ao estender as existentes. Como reportamos na Seção 7, os engenheiros do produto também **apreciam a padronização** introduzida com o DDD — valorizam seguir uma **metodologia de projeto aceita na indústria**, ainda que reconheçam o DDD como **opinionado**.

Concluímos que o **DDD é opção válida** para desenvolver sistemas de software em qualquer situação em que **o domínio de negócio do problema é complexo e precisa ser bem compreendido** para criar software efetivo.

Também concluímos que o **DDD traz certo nível de complexidade e carga cognitiva**, o que cria um **desafio para os engenheiros** — conforme a experiência prévia deles com princípios de OO e sobretudo com DDD, pode variar de **significativamente desafiador** a **fácil de adotar**. Achamos que é um aspecto crucial a considerar num contexto industrial **com compromissos apertados**.

Uma das experiências: **refatorar com DDD não se limita à refatoração do código-fonte — é também uma refatoração da arquitetura**. Pela magnitude, ao grupo fica claro que a refatoração DDD **criará uma quantidade significativa de trabalho** dependendo do tamanho do código-base alvo — aspecto desafiador tanto do ponto de vista do desenvolvimento quanto do negócio. **Os esforços de refatoração devem ser muito bem planejados e executados.**

### 8.1 Aprendizados para a empresa

Para compartilhar a pesquisa, os autores montaram sessões de apresentação na organização, discutindo os benefícios da **linguagem ubíqua** para facilitar a comunicação entre pessoal técnico e não-técnico — e para casar o caso de negócio com o código. Após as medições pós-refatoração, hospedaram sessões de estudo com os engenheiros do time, sobre como pôr o DDD em prática. Soluções encontradas com o time (exemplos): aplicar o DDD **por partes nos módulos** e treinar os engenheiros nos princípios com **códigos de exemplo** (o material de exemplo introduzido pelo estudo).

---

## 9. Ameaças à Validade

Segundo o esquema de classificação de Wohlin et al. (2012):

**Validade de conclusão** — O estudo foi conduzido num time de **pequeno porte** de engenheiros: as conclusões se baseiam nas respostas de um pequeno grupo de participantes por entrevista e questionário, o que pode levantar preocupação quanto à **confiabilidade das medidas** e à **heterogeneidade aleatória dos respondentes**. Porém, pelos **Padrões Empíricos da Pesquisa-Ação**, **é da natureza da pesquisa-ação ter grupo pequeno de participantes**, pois foca num contexto e cenário particulares. Os participantes tinham **conhecimento prévio do código-base**, mas **nível de experiência variável** na indústria e no DDD — o que pode ter impactado percepções e respostas. Medidas foram tomadas para que todos tivessem familiaridade suficiente com o código-base e os conceitos de DDD, permitindo *feedback* informado e significativo.

**Validade interna** — Durante o estudo, **refatorar com DDD não era decisão arquitetural ou de negócio** do produto. O estudo ocorreu num ambiente em que *features* e mudanças de código eram **introduzidas constantemente**; portanto, **isolámos cuidadosamente as ações** desta pesquisa para que os resultados observados **não fossem causados por outras atividades**. Introduzimos a refatoração **num componente isolado** — uma versão de uma **Camada Anticorrupção** (Evans 2003) no código-base (Seção 6) — que **não foi afetado pelas mudanças** no resto do sistema. As perguntas das entrevistas foram escolhidas cuidadosamente para captar as experiências e opiniões dos engenheiros **sem efeito externo** do estudo ou do time de ação. Para eliminar viéses de perguntas desenhadas, também utilizamos o **mTAM** para verificar nossos achados **quantitativamente**. Para eliminar o efeito de maturação nas medições, incluímos os engenheiros novos via **think-aloud**.

*(N.T.: validade de construção e externa também são discutidas no original — págs. 31–32.)*

---

## 10. Conclusão

Nossa pesquisa nos levou a concluir que **uma abordagem de projeto poderosa, como o DDD, é uma ferramenta efetiva para reestruturar e resolver problemas de software** nesta situação. Ela oferece **padronização ao software e aos esforços de refatoração**. Percebemos que o DDD implica **certo grau de complexidade e carga cognitiva**, o que é uma **barreira** para os engenheiros de software — mas que eles estão cientes de seus **benefícios**.

*(N.T.: o trecho da conclusão do artigo termina com a síntese acima; os agradecimentos e as declarações de financiamento seguem no original, págs. 32–33.)*

---

*Fim da tradução. Figuras do original: Fig. 4 (arquitetura do *backend* pós-DDD — dependências), Fig. 5 (arquitetura com classes e contextos delimitados coloridos), Fig. 6 (comparação do score mTAM à curva SUS de Bangor et al. 2009); Tabelas 2, 4, 5, 7 (análise de atributos, avaliação de manutenibilidade ISO/IEC 25010, *statements* do *think-aloud*, mTAM). Referências [1]–[60] no original (págs. 33–35). Os arquivos `.png` das Figuras 4, 5 e demais, extraídos pela ferramenta, estão em `/Users/mathe/Desktop/Modelagem/Artigo 2/.work_emse/figs/`.*