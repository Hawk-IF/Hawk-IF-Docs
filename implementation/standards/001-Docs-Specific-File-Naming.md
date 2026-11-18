# STANDARD-001 — Docs Specific File Naming

**Status:** approved 
**Versão:** 1.0  
**Última atualização:** 18-11-2026  
**Autor:** @Pkpkawe

---

## Objetivo

Este padrão tem como objetivo identificar os arquivos de documentação específicos, por exemplo: um caso de uso específico do frontend.

## Escopo

O padrão se aplica somente ao repositório de documentação.

## Contexto

O repositório tem um design de pastas bem definido; entretanto, seus arquivos funcionam de uma forma geral. Dessa forma, para identificar arquivos que tratam de algo em específico, uma possibilidade seria adicionar mais hierarquias de pastas para representar aquela especificidade. Todavia, essa prática acaba se tornando volumosa, surgindo assim a necessidade de simplificar por meio da nomenclatura dos arquivos.

## Definição do Padrão

O padrão consiste na adição da especificidade na nomenclatura do arquivo, funcionando da seguinte forma:

```text
UC-LoginAdmin.frontend.md
```

Assim, o caso de uso, que já segue o padrão de identificação do tipo de arquivo usando UC, segue de seu título e sua identificação a qual corresponde, que nesse caso é o frontend.

## Exemplos

### Correto

```
UC-LoginAdmin.frontend.md
```

### Incorreto

```
UC-LoginAdmin-Frontend.md
```

## Histórico de Alterações

| Versão | Data | Alteração | Autor |
|---|---|---|---|
| 1.0 | 18-11-2026 | Criação inicial | @Pkpkawe |
