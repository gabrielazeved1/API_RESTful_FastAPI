# User Auth API

API RESTful para gerenciamento de usuários com autenticação JWT, construída com FastAPI.

## Tecnologias

| Ferramenta | Uso |
|---|---|
| **FastAPI** | Framework web e geração automática de docs |
| **SQLAlchemy** | ORM para interação com o banco de dados |
| **Alembic** | Migrações de banco de dados |
| **Pydantic** | Validação de dados e schemas |
| **PyJWT** | Geração e verificação de tokens JWT |
| **pwdlib** | Hashing seguro de senhas (Argon2) |
| **Poetry** | Gerenciamento de dependências |
| **Pytest** | Testes unitários e de integração |
| **Ruff** | Linting e formatação de código |
| **SQLite** | Banco de dados para desenvolvimento |

## Endpoints

| Método | Rota | Descrição | Auth |
|---|---|---|---|
| `GET` | `/` | Mensagem de boas-vindas | Não |
| `POST` | `/users/` | Criar usuário | Não |
| `GET` | `/users/` | Listar usuários | Não |
| `PUT` | `/users/{id}` | Atualizar usuário | Sim |
| `DELETE` | `/users/{id}` | Deletar usuário | Sim |
| `POST` | `/token` | Gerar token JWT | Não |

## Configuração

### Pré-requisitos

- Python 3.11+
- Poetry

### 1. Clonar o repositório

```bash
git clone git@github.com:gabrielazeved1/API_RESTful_FastAPI.git
cd API_RESTful_FastAPI
```

### 2. Instalar dependências

```bash
poetry install
```

### 3. Variáveis de ambiente

Copie o arquivo de exemplo e preencha os valores:

```bash
cp .env.sample .env
```

```ini
DATABASE_URL="sqlite:///database.db"
SECRET_KEY="sua_chave_secreta_aqui"
ALGORITHM="HS256"
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

### 4. Migrações do banco de dados

```bash
poetry run alembic upgrade head
```

### 5. Executar

```bash
poetry run task run
```

Acesse em: [http://127.0.0.1:8000](http://127.0.0.1:8000)

Documentação interativa: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

## Testes

```bash
poetry run task test
```

Arquivos de teste:

- `tests/test_app.py` — endpoints da API
- `tests/test_db.py` — operações no banco de dados
- `tests/test_security.py` — hashing e JWT
- `tests/conftest.py` — fixtures com banco SQLite em memória

## Qualidade de código

```bash
# Verificar problemas
poetry run task lint

# Corrigir automaticamente
poetry run task pre_format

# Formatar
poetry run task format
```

## Estrutura do projeto

```
user_auth_api/
├── app.py         # Rotas e endpoints
├── database.py    # Conexão com o banco
├── models.py      # Modelos SQLAlchemy
├── schemas.py     # Schemas Pydantic
├── security.py    # JWT e hashing
└── settings.py    # Variáveis de ambiente
migrations/        # Migrações Alembic
tests/             # Suite de testes
```
