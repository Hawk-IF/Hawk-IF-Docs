# Architecture

Esta é a documentação arquitetural do sistema. Este guia serve como ponto de partida para compreender a organização técnica, as decisões estruturais, as integrações e a infraestrutura do projeto.

---

## Como navegar nesta seção

Utilize o índice abaixo para encontrar rapidamente o tipo de documentação que você precisa:

| Diretório / Arquivo | Propósito Principal | Quando consultar? |
| :--- | :--- | :--- |
| **[diagrams/](./diagrams/)** | Representações visuais (C4, UML, fluxos, infraestrutura). | Quando precisar visualizar a estrutura, fluxos de dados ou comunicação entre módulos. |
| **[adr/](./adr/)** | *Architecture Decision Records* (decisões, motivos e impactos). | Quando quiser entender o **"porquê"** de uma escolha técnica ou avaliar alternativas já descartadas. |
| **[patterns/](./patterns/)** | Padrões estruturais, modularização e convenções internas. | Antes de criar novos módulos ou funcionalidades, para manter a consistência do código. |
| **[integrations/](./integrations/)** | Comunicação externa, APIs terceiras, webhooks e autenticação. | Ao desenvolver ou depurar integrações com serviços fora do ecossistema principal (como o Home Assistant). |
| **[infrastructure/](./infrastructure/)** | Deploy, containers, cloud, redes, CI/CD e observabilidade. | Para configurar ambientes, provisionar IaC ou investigar métricas e logs. |

---

## Visão Geral

O projeto é estruturado de forma desacoplada, mantendo o **frontend** e o **backend** independentes entre si. A orquestração e a conexão entre todas as partes do ecossistema são gerenciadas por meio de **Infraestrutura como Código (IaC)**, que atua como elo tanto para as aplicações internas quanto para serviços externos, como o **Home Assistant**.

### 1. Estrutura e Estratégia Arquitetural

A estratégia arquitetural divide-se conforme a responsabilidade de cada camada do sistema:

* **Frontend (Clean Architecture + Ports and Adapters):** Estruturado com foco no isolamento das regras de negócio da interface e de frameworks externos, garantindo testabilidade e baixo acoplamento.
* **Backend (Arquitetura em Camadas):** Organizado de forma modular em camadas bem definidas (ex: apresentação/rotas, serviços/regras de negócio e acesso a dados), facilitando a manutenção e a evolução da API.
* **Conectividade e Orquestração (IaC):** Toda a comunicação de rede, exposição de serviços e integração entre as aplicações internas e o Home Assistant é declarada e gerenciada via código.

### 2. Principais Componentes

* **Frontend:** Interface do usuário responsável pela interação e visualização dos dados, consumindo os serviços expostos pelo backend.
* **Backend:** API central responsável pelo processamento das regras de negócio, persistência de dados e intermediação com serviços externos.
* **Infraestrutura como Código (IaC):** Camada de provisionamento e rede que interliga o frontend, o backend, o banco de dados e as integrações externas.
* **Home Assistant:** Serviço externo integrado ao ecossistema para automação e troca de eventos/estados.

### 3. Fluxos Principais

Os fluxos de comunicação ocorrem de ponta a ponta atravessando a rede gerenciada pela IaC:
* **Fluxo Interno:** O usuário interage com o **Frontend**, que realiza requisições HTTP/REST para o **Backend**, o qual processa a regra de negócio e persiste/consulta informações no **PostgreSQL**.
* **Fluxo Externo:** A comunicação entre o **Backend** e o **Home Assistant** ocorre por meio das rotas e conectores configurados na infraestrutura.

### 4. Stack Tecnológica

Resumo das principais tecnologias utilizadas na base do projeto:

* **Backend:** Python, FastAPI
* **Frontend:** TypeScript, React
* **Banco de Dados:** PostgreSQL, Redis
* **Integrações Externas:** Home Assistant