# Contribuindo com este Projeto

Siga as etapas abaixo para configurar o ambiente local e visualizar o site com o **MkDocs**.

## 🧰 Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [Git](https://git-scm.com/)
- [Python 3.12+](https://www.python.org/downloads/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/)
- [Chave SSH do Github configurada](https://www.youtube.com/watch?v=dWj3JEpM6nQ)

## ⚙️ Passos para rodar o projeto localmente

### 1. Clonar o repositório

```bash
git git@github.com:inct-labplan/site-governanca.git
cd site-governanca
```

### 2. Criar ambiente virtual e instalar dependências

```bash
uv sync
```

### 3. Rodar o site localmente com MkDocs

> Use o comando mkdocs serve para rodar o servidor local e ver suas alterações em tempo real no navegador.

```bash
cd site-governanca
uv run mkdocs serve
```
Depois disso, o site estará disponível em: [http://127.0.0.1:8000](http://127.0.0.1:8000)
