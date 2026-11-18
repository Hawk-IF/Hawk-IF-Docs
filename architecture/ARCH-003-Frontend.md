# ARCH-003: Frontend

**Status:** approved  
**Versão:** 1.0  
**Última atualização:** 18-11-2026
**Autor:** @Pkpkawe

---

## Visão Geral

O **Frontend** é a camada de apresentação e interação com o usuário do sistema, desenvolvida de forma totalmente desacoplada do backend. Seu objetivo é fornecer uma interface responsiva, intuitiva e segura para visualização de dados, acionamento de comandos e gerenciamento de estado da aplicação.

### Principais Responsabilidades
- Renderizar a interface gráfica e gerenciar a experiência do usuário (UI/UX).
- Validar dados de entrada no lado do cliente antes do envio à API.
- Gerenciar o estado global e local da sessão (autenticação, preferências, cache de requisições).
- Comunicar-se com o **Backend** por meio de requisições HTTP/REST orquestradas pela infraestrutura do projeto.

---

## Estilo Arquitetural

### Clean Architecture & Hexagonal (Ports and Adapters)

O frontend combina os princípios da **Clean Architecture** com o padrão **Ports and Adapters (Arquitetura Hexagonal)** para isolar completamente o núcleo da aplicação (domínio e casos de uso) de detalhes externos, como o framework React/Vite e clientes HTTP.

- **Regra de Dependência:** As dependências apontam sempre de fora para dentro. A camada de `infraestructure` (adaptadores de entrada e saída) depende dos contratos (`ports`) definidos na camada de `application`, que por sua vez orquestra o `domain`. O núcleo não conhece o React ou o Axios.
- **Benefícios:** Alta testabilidade (casos de uso testáveis sem interface gráfica), isolamento de framework (o React fica contido como um adaptador de entrada `web`) e facilidade para trocar bibliotecas de comunicação externa.

---

## Estrutura Geral do Sistema

A aplicação é organizada em três camadas concêntricas principais, apoiadas por um núcleo compartilhado (`core`):

1. **Domain (Domínio):** Entidades centrais da aplicação, regras de validação puras e exceções de domínio (TypeScript puro).
2. **Application (Aplicação):** Casos de uso da interface (ex: *Realizar Login*, *Listar Dispositivos*) e definição dos contratos (**Ports**) de entrada (`input`) e saída (`output`).
3. **Infrastructure (Infraestrutura):** Adaptadores concretos (**Adapters**) que conectam o núcleo ao mundo externo:
   * **Input (`web`):** A aplicação React/Vite que aciona os casos de uso através das portas de entrada.
   * **Output (`api`):** Clientes HTTP (Axios/Fetch) e storage que implementam as portas de saída.

```text
src/
├── core/               # Núcleo compartilhado do sistema
├── domain/             # Regras de negócio puras
│   ├── entities/       # Entidades de domínio
│   └── exceptions/     # Exceções de domínio
├── application/        # Casos de uso (orquestração do domínio)
│   ├── ports/          # Interfaces (contratos) de entrada e saída
│   │   ├── input/      # Portas de entrada (ex: interfaces dos casos de uso)
│   │   └── output/     # Portas de saída (ex: interfaces de repositórios/APIs)
│   └── usecases/       # Implementação dos casos de uso
└── infraestructure/    # Adaptadores (implementações concretas dos ports)
    └── adapters/
        ├── input/      # Entradas: Web (UI), etc.
        │   └── web/    # Aplicação React (root do Vite)
        └── output/     # Saídas: HTTP clients, storage, etc.
            └── api/    # Cliente HTTP (Axios, etc.)
```

---

## Componentes

| Componente | Responsabilidade | Entrada | Saída | Tecnologia |
| --- | --- | --- | --- | --- |
| **Input Adapter (`web`)** | Renderização visual, captura de eventos do usuário e gerenciamento de estado de tela. | Props, eventos de UI e respostas das portas de entrada. | Elementos DOM e chamadas às `input ports`. | React, Vite, TypeScript |
| **Ports (`input` / `output`)** | Contratos (interfaces) que desacoplam os adaptadores externos da lógica da aplicação. | Assinaturas de métodos e DTOs. | Contratos tipados para implementação ou consumo. | TypeScript |
| **Use Cases (`application`)** | Orquestração da lógica de negócio da interface, validações e tratamento de exceções. | DTOs vindos do adaptador `web` via `input port`. | Entidades de domínio e chamadas às `output ports`. | TypeScript |
| **Domain (`entities` / `exceptions`)** | Representação das regras de negócio puras e erros específicos do domínio. | Dados brutos para instanciação/validação. | Entidades válidas ou exceções de domínio. | TypeScript |
| **Output Adapter (`api`)** | Implementação das portas de saída para comunicação HTTP com o Backend e injeção de headers. | Endpoint, payload e token de autenticação. | Resposta JSON mapeada ou erro padronizado. | Axios / Fetch |

---

## Fluxo Geral

1. **Interação (`Input Adapter - web`):** O usuário interage com um componente React na aplicação Vite (ex: preenche um formulário e clica em enviar).
2. **Acionamento (`Input Port`):** A interface aciona um caso de uso através de sua interface definida em `application/ports/input`.
3. **Orquestração (`Use Case` & `Domain`):** A implementação em `application/usecases` valida os dados utilizando as entidades e regras de `domain` e solicita dados externos através de uma interface em `application/ports/output`.
4. **Requisição Externa (`Output Adapter - api`):** O adaptador concreto em `infraestructure/adapters/output/api` executa a chamada HTTP para o **Backend** (roteado pela rede definida na IaC).
5. **Atualização da UI:** A resposta da API retorna pelo fluxo inverso até o adaptador `web`, que atualiza o estado do React e re-renderiza a interface para o usuário.

---

## Riscos Conhecidos

- **Over-engineering (Complexidade excessiva):** A aplicação estrita de Clean Architecture + Ports & Adapters no frontend pode gerar excesso de arquivos, interfaces e mapeadores (*mappers*) para telas simples (CRUDs básicos).
  - *Impacto:* Aumento no tempo de desenvolvimento inicial e curva de aprendizado para novos desenvolvedores.
  - *Solução:* Adotar pragmatismo — manter entidades e casos de uso enxutos para fluxos simples, aplicando abstrações completas apenas onde há regras de negócio complexas ou alta volatilidade da API.
- **Dessincronização de contratos com o Backend:** Mudanças nos schemas da API FastAPI podem quebrar a tipagem no TypeScript em tempo de execução.
  - *Impacto:* Erros inesperados na renderização de componentes ou falhas nos adaptadores de saída.
  - *Solução:* Gerar tipos automaticamente a partir do OpenAPI/Swagger do FastAPI ou validar respostas na camada `adapters/output/api`.

---

## Observações

- Todas as variáveis de ambiente (como a URL base da API) são injetadas em tempo de build ou via configuração de container definida na infraestrutura como código.

---

## Histórico de Alterações

| Versão | Data | Alteração | Autor |
|---|---|---|---|
| 1.0 | 18-11-2026 | Criação inicial da arquitetura do Frontend | @Pkpkawe |

---

## Referências

- Martin, Robert C. *Clean Architecture: A Craftsman's Guide to Software Structure and Design*.
- Cockburn, Alistair. *Hexagonal Architecture (Ports and Adapters)*.
- Documentação oficial do React — [react.dev](https://react.dev)
- Documentação oficial do Vite — [vite.dev](https://vite.dev)