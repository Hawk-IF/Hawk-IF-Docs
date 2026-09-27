# Hawk-IF
O Hawk If é um sistema de gerenciamento de salas
automatizado que funciona atraves de sensores colocados 
em cada sala, ele permite ver o status de um sala e agendar seu uso
junto a um gerenciamento de seus recursos, Esse repositorio
é responsavel pela documentação do sistema, e esse readme
contem os dados minimos de todos os repositorios.

se quiser saber sobre a estrutura da documentação va no [sumario](./SUMARRY.md)
e se quiser acompanhar as atualizações va no [changelog](./changelog.md)
# Hawk-If-Frontend
não ha nada aqui ainda

# Hawk-IF-Backend
Backend do [Hawk IFRN](https://github.com/Hawk-IF/) criado com 
python e utilizando fastapi

## Sumario
- [Docs](#documentação-e-readme)
- [Rodando o Projeto](#como-rodar)

## Documentação e readme
O sistema tem seu proprio [repositorio de documentação](https://github.com/Hawk-IF/Hawk-IF-Docs)
o repositorio do backend apenas tem alguns arquivos minimos como o 
readme, para dar suporte rapido sem a necessidade de abrir outro repositorio
ou buscar dentro de pastas e arquivos gigantes


## Como Rodar
O sistema tem alguns requisitos minimos para rodar:

### Requisitos
- python (versão no arquivo [.python-version](.python-version))
- uv ou pip para gerenciar as dependencias do python
- postgresql
- git e github

### Clonando o repositorio
para clonar o repositorio basta rodar:

```bash
git clone https://github.com/Hawk-IF/Hawk-IF-Backend ./backend
```

### Baixando das dependencias do python:
com o uv use:

```bash
uv sync
```

# Hawk-If-Infra
não ha nada aqui ainda