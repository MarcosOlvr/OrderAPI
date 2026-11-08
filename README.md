
# OrderAPI

API REST para gerenciamento de pedidos, desenvolvida em Python com FastAPI, SQLite e autenticação baseada em JWT.

O projeto tem como objetivo aplicar boas práticas no desenvolvimento de APIs, incluindo organização modular do código, validação de dados, autenticação de usuários e controle de acesso por permissões.

## Funcionalidades

- **Autenticação com JWT:** geração e validação de tokens de acesso.
- **Gerenciamento de usuários:** cadastro e autenticação de usuários.
- **Gerenciamento de pedidos:** operações relacionadas à criação e ao gerenciamento de pedidos.
- **Controle de acesso:** diferenciação de permissões entre usuários comuns e administradores.
- **Proteção de senhas:** utilização de bcrypt para armazenamento seguro de senhas por meio de hash.
- **Validação de dados:** utilização de schemas com Pydantic.
- **Persistência de dados:** armazenamento em banco de dados SQLite.
- **Migrações de banco de dados:** utilização do Alembic para gerenciar alterações na estrutura do banco.

## Tecnologias utilizadas

| Tecnologia | Finalidade |
|---|---|
| Python | Linguagem de programação |
| FastAPI | Desenvolvimento da API REST |
| SQLAlchemy | ORM |
| SQLite | Banco de dados |
| Pydantic | Validação e estruturação de dados |
| Alembic | Gerenciamento de migrações |
| JWT | Autenticação baseada em tokens |
| bcrypt | Hash de senhas |

## Estrutura do projeto

```text
OrderAPI/
├── alembic/             # Migrações do banco de dados
├── auth_routes.py       # Rotas de autenticação
├── order_routes.py      # Rotas de pedidos
├── dependencies.py      # Dependências e controle de acesso
├── models.py            # Modelos do banco de dados
├── schemas.py           # Schemas e validação de dados
├── main.py              # Ponto de entrada da aplicação
├── requirements.txt     # Dependências Python
├── .env                 # Variáveis de ambiente
└── README.md
```

## Instalação e configuração

### 1. Clone o repositório

```bash
git clone https://github.com/MarcosOlvr/OrderAPI.git
cd OrderAPI
```

### 2. Crie um ambiente virtual

```bash
python -m venv .venv
```

Ative o ambiente virtual.

### 3. Instale as dependências

```bash
python -m pip install -r requirements.txt
```

### 4. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto e configure as variáveis necessárias:

```env
SECRET_KEY=sua_chave_secreta
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

| Variável | Descrição |
|---|---|
| `SECRET_KEY` | Chave secreta utilizada para assinar e validar tokens JWT. |
| `ALGORITHM` | Algoritmo utilizado na assinatura dos tokens. |
| `ACCESS_TOKEN_EXPIRE_MINUTES` | Tempo de validade do token, em minutos. |

Os valores apresentados são exemplos. Confirme o algoritmo aceito pelo projeto e ajuste o tempo de expiração conforme necessário.

### 5. Execute a aplicação

Se o arquivo `main.py` expuser a instância FastAPI com o nome `app`, execute:

```bash
uvicorn main:app --reload
```

## Documentação da API

Com a aplicação em execução na porta padrão `8000`, acesse:

- **Swagger UI:** [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

A documentação interativa permite consultar as rotas, visualizar os schemas e testar as requisições disponibilizadas pela API.

## Autenticação e autorização

A API utiliza JSON Web Tokens (JWT) para autenticação.

Em endpoints protegidos, o token costuma ser enviado no cabeçalho HTTP:

```http
Authorization: Bearer <seu_token>
```

## Banco de dados e migrações

O projeto utiliza SQLite para persistência de dados e SQLAlchemy para interação com o banco.

O Alembic é utilizado para gerenciar migrações da estrutura do banco de dados.

Caso a configuração esteja preparada para utilizar o Alembic diretamente, as migrações podem ser aplicadas com:

```bash
alembic upgrade head
```

Antes de executar o comando, confirme se a configuração do Alembic e a URL do banco estão corretas.