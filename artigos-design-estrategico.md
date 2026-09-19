# Escolha de Artigos — Design Estratégico com Mapeamento de Relações entre Contextos

**Disciplina:** Modelagem de Domínio (FACOM33505 — 2026/2, prof. Victor Sobreira)
**Tema (item 5.2 do programa):** Design Estratégico e Mapeamento de Contextos — Relações entre Domínios: Núcleo Compartilhado (Shared Kernel), Cliente-Fornecedor (Customer/Supplier), Parceria (Partnership), Conformista (Conformist)
**Data da pesquisa:** 19/09/2026
**Bases consultadas:** OpenAlex, Semantic Scholar, CrossRef, DuckDuckGo (Google Scholar indisponível por bloqueio anti-bot no momento da consulta)

---

## OPÇÃO PRINCIPAL

### Título
**Domain-specific Language and Tools for Strategic Domain-driven Design, Context Mapping and Bounded Context Modeling**

- **Autores:** Stefan Kapferer e Olaf Zimmermann (University of Applied Sciences of Eastern Switzerland — HSR/OST, Rapperswil, Suíça)
- **Veículo:** *Proceedings of the 8th International Conference on Model-Driven Engineering and Software Development* (MODELSWARD 2020), SCITEPRESS
- **Páginas:** 299–306 (8 páginas)
- **ISBN:** 978-989-758-400-8 | **ISSN:** 2184-4348
- **Link público:** https://doi.org/10.5220/0008910502990306
- **Arquivo local:** `TRABALHO DE MODELAGEM/89105.pdf`

### Relação com o tema
Aderência **literal** ao subitem 5.2 do plano de ensino. O artigo:
1. Destila um **meta-modelo dos padrões estratégicos do DDD** a partir da literatura (Evans 2003; Vernon 2013), resolvendo ambiguidades e combinações entre eles;
2. Define sintaxe formal (DSL — CML) para **todas as relações pedidas no tema**: Parceria (`[P]<->[P]`), Núcleo Compartilhado (`[SK]<->[SK]`), Genérica Upstream-Downstream, **Cliente-Fornecedor** (`[S]/[C]`), Conformista (`[D,CF]`/`[U,OHS,PL]`), Camada Anti-Corrupção (`[D,ACL]`), Open Host Service e Published Language — com exemplos completos em um estudo de caso de seguros;
3. Apresenta o **Context Mapper**, ferramenta open source (https://contextmapper.org) que modela, valida, refatora e transforma Context Maps (geração de diagramas PlantUML/UML e contratos de serviço MDSL).

### Categoria
**Estado da arte** — consolida e esclarece os padrões estratégicos do DDD a partir da literatura, propõe um meta-modelo unificado e uma ferramenta com validação empírica (prototipação, action research e estudos de caso). O seminal do tema (Evans, *Domain-Driven Design*, 2003) é livro, não artigo, e será citado na apresentação como origem dos padrões.

### Indicadores de relevância (verificados em 19/09/2026)
| Indicador | Valor | Fonte |
|---|---|---|
| Citações | **21** | Semantic Scholar |
| Citações | 19 | OpenAlex |
| Veículo | Conferência internacional estabelecida (MODELSWARD, 8ª edição; indexada, DOI/ISBN/ISSN) | CrossRef |
| Produtos derivados | Ferramenta **Context Mapper** open source em uso contínuo (contextmapper.org), plugin Eclipse, DSL CML adotada como fundação de trabalhos posteriores (SoSyM/CCIS), geradores PlantUML e MDSL | Artigo + site oficial |
| Patentes | Não se aplica (contribuição acadêmica open source) | — |

### Motivações da escolha
- É o único artigo encontrado cujo **título e conteúdo cobrem exatamente o tema**: "Strategic Domain-driven Design, **Context Mapping** and Bounded Context Modeling";
- Apresenta as **quatro relações do sub-item 5.2** com sintaxe, semântica, exemplo e regras de combinação — material ideal para uma apresentação com ilustrações e trechos de código CML;
- Ferramenta open source permite **demo ao vivo** na apresentação (critério "preparação/domínio" da avaliação);
- Idade (2020) e citações (~21) coerentes com estado da arte de um padrão de nicho; linha de pesquisa ativa dos autores (versões subsequentes mais citadas).

---

## �OPÇÃO SECUNDÁRIA (versão estendida da mesma linha)

### Título
**Domain-driven Service Design: Context Modeling, Model Refactoring and Contract Generation**

- **Autores:** Stefan Kapferer e Olaf Zimmermann (HSR/OST, Suíça)
- **Veículo:** *Service-Oriented Computing* (SummerSoC 2020), Springer **CCIS**, vol. 1277
- **Páginas:** 189–208 (20 páginas)
- **Link público:** https://doi.org/10.1007/978-3-030-64846-6_11
- **Arquivo local:** `TRABALHO DE MODELAGEM/Kapferer-Zimmermann_2020_Domain-Driven-Service-Design_SummerSoC_AuthorsCopy.pdf` (authors' copy oficial, baixada de contextmapper.org)

### Relação com o tema — mapeamento padrão a padrão (verificado no texto integral)

O objeto central do artigo é o Context Map: *"A Context Map specifies the relationships between the Bounded Contexts and how they interact with each other"* (Tabela 1). A Seção 2.1 classifica as relações na mesma taxonomia da disciplina: **Partnership e Shared Kernel são relações simétricas; Customer/Supplier, Conformist e ACL são relações Upstream-Downstream**.

| Padrão do tema | Definição formal no artigo (Tabela 1) | Modelagem concreta (Listing 2.1, CML) |
|---|---|---|
| **Parceria (P)** | Relação simétrica e cooperativa em que os dois contextos "só podem ter sucesso ou falhar juntos" + planejamento coordenado | `PolicyManagement <-> [P] RiskManagement` |
| **Núcleo Compartilhado (SK)** | Relação íntima em que dois contextos "compartilham parte de seus modelos de domínio"; simétrica, tipicamente biblioteca compartilhada mantida pelas duas equipes | `CustomerSelfService [SK] <-> [SK] PolicyManagement` |
| **Cliente-Fornecedor (C/S)** | Upstream-Downstream em que o downstream influencia o upstream; o fornecedor respeita os requisitos do cliente e ajusta seu planejamento | `CustomerSelfService [C] <- [S] CustomerManagement` |
| **Conformista (CF)** | Downstream que adota o modelo do upstream em vez de traduzi-lo | `CustomerCore [OHS, PL] -> [CF] CustomerSelfService` |
| **(+ ACL)** | Camada que traduz entre o modelo do upstream e o domínio do downstream | `CustomerCore [OHS, PL] -> [ACL] PolicyManagement` |

Três diferenciais para a apresentação:
1. **Meta-modelo com regras de combinação** — define quais combinações de padrões fazem sentido (regras semânticas implementadas na ferramenta), respondendo à ambiguidade deixada por Evans;
2. **Exemplo único com todos os padrões** — o Context Map do projeto *Lakeside Mutual* (seguros, Fig. 1) contém P, SK, C/S, CF e ACL no mesmo diagrama — ideal para ilustrações;
3. **Da relação ao código** — Seção 3.3: upstream → *API provider*, downstream → *API client* (Tabela 2), com geração de contratos MDSL — material para as conclusões pessoais correlacionando com a disciplina.

Além disso, o artigo adiciona 7 **Architectural Refactorings** (split/merge de Bounded Contexts e Aggregates) e um método de decomposição passo a passo — o "como evoluir" o mapa de contextos, complemento natural das relações estáticas do artigo MODELSWARD.

### Categoria
**Estado da arte** (com forte componente prática — refactorings e método aplicados em estudos de caso e action research com parceiros industriais).

### Indicadores de relevância (verificados em 19/09/2026)
| Indicador | Valor | Fonte |
|---|---|---|
| Citações | **15** | Semantic Scholar |
| Citações | 26 | OpenAlex |
| Veículo | Springer CCIS (série LNCS, peer review) | CrossRef |
| Produtos derivados | Context Mapper, catálogo de Architectural Refactorings, MDSL (Microservice Domain-Specific Language) | Artigo + contextmapper.org |

### Motivação
Maior profundidade (20 págs.) e veículo Springer; ideal se o grupo quiser apresentar também **decomposição e evolução** de contextos, não apenas as relações. Escolher **um** dos dois (mesma linha; apresentar ambos seria redundante).

---

## Artigos avaliados e descartados (filtragem título/resumo → conclusões)

| Arquivo na pasta | Motivo do descarte |
|---|---|
| `25274-Texto del artículo…` | Usa DDD **tático** em app de gestão de horários; veículo fraco (Ciencia Latina); "termos similares em outros contextos" |
| `2608.02644v1.pdf` / `2608.02644v1-2.pdf` | Identificação de microsserviços via feature model; **preprint arXiv sem peer review** |
| `2609.13048v1.pdf` | Scheduling de microsserviços com aprendizado por reforço — sem relação com mapeamento de contextos |
| `3828669.pdf` (ACM TOSEM) | CI/falhas em microsserviços — veículo forte, tema fora do escopo |
| `software-04-00006-with-cover.pdf` | IA no design de microsserviços (MDPI); DDD só citado de passagem |
| `A_Systematic_Literature_Review_on_AI-Driven_Migration…` (IEEE Access) | Migração monolito→micro com IA; sem foco em relações entre contextos |
| `Design_and_decomposition_of_Microservices_Architecture…` (TASK Quarterly) | SLR de decomposição genérica |
| `Stefan-Kapferer_SummerSoC2020_presentation.pdf` | Slides da palestra (apoio visual p/ apresentação), não é artigo |

---

## Fontes

1. Kapferer & Zimmermann (2020). *Domain-specific Language and Tools for Strategic Domain-driven Design, Context Mapping and Bounded Context Modeling.* MODELSWARD 2020, p. 299–306. https://doi.org/10.5220/0008910502990306
2. Kapferer & Zimmermann (2020). *Domain-driven Service Design: Context Modeling, Model Refactoring and Contract Generation.* SummerSoC 2020 / Springer CCIS v.1277, p. 189–208. https://doi.org/10.1007/978-3-030-64846-6_11
3. Semantic Scholar API — contagens de citação (api.semanticscholar.org), consulta em 19/09/2026.
4. OpenAlex API — contagens de citação e metadados de veículo (api.openalex.org), consulta em 19/09/2026.
5. CrossRef API — metadados editoriais (container, páginas, ISBN/ISSN), consulta em 19/09/2026.
6. Context Mapper (projeto open source): https://contextmapper.org/
7. Plano de ensino FACOM33505 (SEI 7664281), item 5.2.
