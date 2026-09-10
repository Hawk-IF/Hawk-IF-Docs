# SUMMARY

Este documento funciona como índice geral da documentação do projeto Neburos, centralizando a navegação entre os diferentes módulos, artefatos e áreas do sistema.

## Estrutura Geral

```
docs/
├── README.md
├── SUMMARY.md
│ 
├── _templates/
│ 
├── organization/ 
│   ├── overview.md 
│   ├── team.md 
│   ├── methodology.md 
│   ├── onboarding.md 
│   └── contribution.md
│ 
├── architecture/
│   ├── overview.md
│   ├── diagrams/
│   ├── adr/
│   ├── patterns/
│   ├── integrations/
│   └── infrastructure/
│ 
├── business/
│   ├── glossary/
│   ├── domains/
│   ├── rules/
│   ├── workflows/
│   └── validations/
│ 
├── use-cases/
│ 
├── implementation/
│   ├── standards/
│   ├── guides/
│   ├── runbooks/
│   ├── testing/
│   ├── security/
│   └── performance/
│ 
├── requirements/
│   ├── functional/
│   └── non-functional/
│ 
└── references/
    ├── external-links/
    ├── research/
    └── inspirations/
```

## [README.md](./README.md)

Documento principal do repositório: 

---

## [organization/](./organization/)

Documentação organizacional do projeto, equipe e fluxo de desenvolvimento.

### Estrutura

#### [overview.md](./organization/overview.md)

Visão geral organizacional do projeto.

Define:
- estrutura organizacional;
- áreas do projeto;
- organização geral da equipe;
- responsabilidades macro.

#### [team.md](./organization/team.md)

Documento da equipe do projeto.

Contém:
- membros;
- cargos;
- responsabilidades;
- áreas de atuação;
- contatos;
- perfis GitHub.

#### [methodology.md](./organization/methodology.md)

Metodologias e fluxo de trabalho utilizados no projeto.

Exemplos:
- Scrum;
- GitFlow;
- code review;
- branching;
- organização das entregas;
- cerimônias.

#### [onboarding.md](./organization/onboarding.md)

Guia de entrada de novos colaboradores.

Contém:
- setup inicial;
- ferramentas;
- acessos;
- fluxo inicial;
- leitura obrigatória;
- primeiros passos.

#### [contribution.md](./organization/contribution.md)

Regras e padrões de contribuição do projeto.

Exemplos:
- commits;
- pull requests;
- revisão de código;
- boas práticas;
- padrões obrigatórios.

---

## [_templates/](./_templates/)

Contém templates padronizados utilizados para criação dos documentos do projeto.

Exemplos:
- ADRs;
- requisitos;
- regras de negócio;
- runbooks;
- guias;
- casos de uso.

---

## [architecture/](./architecture/)

Documentação arquitetural do sistema.

### Estrutura

#### [overview.md](./architecture/overview.md)

Visão geral da arquitetura do sistema:
- estrutura;
- componentes;
- fluxos;
- tecnologias;
- estratégias arquiteturais.

#### [diagrams/](./architecture/diagrams/)

Diagramas técnicos e arquiteturais.

Exemplos:
- C4;
- UML;
- sequência;
- fluxos;
- infraestrutura.

#### [adr/](./architecture/adr/)

Architecture Decision Records (ADRs).

Documenta:
- decisões arquiteturais;
- motivos;
- impactos;
- alternativas consideradas.

#### [patterns/](./architecture/patterns/)

Padrões arquiteturais e estruturais adotados no sistema.

Exemplos:
- modularização;
- clean architecture;
- convenções estruturais;
- organização interna.

#### [integrations/](./architecture/integrations/)

Integrações externas e comunicação entre sistemas.

Exemplos:
- APIs externas;
- autenticação;
- webhooks;
- serviços terceiros.

#### [infrastructure/](./architecture/infrastructure/)

Infraestrutura do sistema.

Contém:
- deploy;
- containers;
- ambientes;
- cloud;
- CI/CD;
- redes;
- observabilidade.

---

## [business/](./business/)

Documentação relacionada às regras e funcionamento do negócio.

### Estrutura

#### [glossary/](./business/glossary/)

Glossário oficial de termos utilizados no sistema.

Define:
- conceitos;
- entidades;
- nomenclaturas;
- significados de negócio.

#### [domains/](./business/domains/)

Divisão dos domínios do sistema.

Documenta:
- responsabilidades;
- limites;
- entidades;
- interações entre domínios.

#### [rules/](./business/rules/)

Regras de negócio do sistema.

Define:
- comportamentos;
- restrições;
- decisões;
- regras condicionais.

#### [workflows/](./business/workflows/)

Fluxos operacionais e processos do negócio.

Documenta:
- processos;
- sequências operacionais;
- interações;
- fluxos de execução.

#### [validations/](./business/validations/)

Regras de validação aplicadas no sistema.

Exemplos:
- validação de dados;
- restrições de entrada;
- verificações obrigatórias.

---

## [use-cases/](./use-cases/)

Documentação dos casos de uso do sistema.

Define:
- interações entre usuário e sistema;
- fluxos principais;
- fluxos alternativos;
- comportamentos esperados.

---

## [implementation/](./implementation/)

Documentação técnica relacionada ao desenvolvimento e manutenção do sistema.

### Estrutura

#### [standards/](./implementation/standards/)

Padrões e convenções técnicas do projeto.

Exemplos:
- nomenclatura;
- organização;
- estrutura de código;
- boas práticas.

#### [guides/](./implementation/guides/)

Guias e tutoriais técnicos.

Exemplos:
- setup;
- configuração;
- criação de módulos;
- processos de desenvolvimento.

#### [runbooks/](./implementation/runbooks/)

Procedimentos operacionais.

Exemplos:
- incidentes;
- manutenção;
- rollback;
- recuperação;
- operação de infraestrutura.

#### [testing/](./implementation/testing/)

Estratégias e documentação de testes.

Exemplos:
- testes unitários;
- integração;
- E2E;
- cobertura;
- validação automatizada.

#### [security/](./implementation/security/)

Documentação relacionada à segurança do sistema.

Exemplos:
- autenticação;
- autorização;
- criptografia;
- proteção contra vulnerabilidades;
- políticas de segurança.

#### [performance/](./implementation/performance/)

Estratégias de otimização e desempenho.

Exemplos:
- cache;
- otimização;
- filas;
- performance de queries;
- escalabilidade.

---

## [requirements/](./requirements/)

Documentação oficial dos requisitos do sistema.

### Estrutura

#### [functional/](./requirements/functional/)

Requisitos funcionais (RFs).

Define funcionalidades do sistema.

Exemplos:
- autenticação;
- cadastro;
- gerenciamento financeiro;
- relatórios.

#### [non-functional/](./requirements/non-functional/)

Requisitos não funcionais (RNFs).

Define:
- segurança;
- performance;
- disponibilidade;
- confiabilidade;
- escalabilidade;
- observabilidade.

---

## [references/](./references/)

Materiais auxiliares utilizados no projeto.

### Estrutura

#### [external-links/](./references/external-links/)

Links e documentações externas úteis.

#### [research/](./references/research/)

Pesquisas técnicas, estudos e análises relacionadas ao projeto.

#### [inspirations/](./references/inspirations/)

Projetos, ideias e referências utilizadas como inspiração para o desenvolvimento do sistema.