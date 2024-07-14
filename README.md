# Hackathon-Desafio-II

# API REST AdventureWorks com FastAPI

Este projeto desenvolve uma API REST usando FastAPI para interagir com o banco de dados AdventureWorks. A API oferece funcionalidades CRUD para produtos, autenticação e autorização, paginação, filtragem, ordenação, manipulação de transações, criação de logs e documentação automática.

## Estrutura do Projeto

- `main.py`: Arquivo principal que inicia a aplicação FastAPI.
- `models.py`: Define os modelos de banco de dados usando SQLAlchemy.
- `schemas.py`: Define os schemas de dados usando Pydantic.
- `crud.py`: Contém as funções CRUD para interação com o banco de dados.
- `auth.py`: Implementa autenticação e autorização usando JWT.
- `routers/`: Contém os arquivos de roteamento para organizar as rotas da API.
- `tests/`: Contém testes unitários e de integração usando PyTest.

## Funcionalidades

### Funcionalidades Básicas

- **Create**: Rota POST `/products/` que aceita um corpo de requisição com detalhes do produto e adiciona o novo produto à tabela de produtos.
- **Read**: Rota GET `/products/` que retorna uma lista de todos os produtos com paginação, filtragem e ordenação. Rota GET `/products/{id}` que retorna os detalhes de um único produto baseado no ID do produto.
- **Update**: Rota PUT `/products/{id}` que aceita um corpo de requisição com detalhes do produto e atualiza o produto com o ID correspondente.
- **Delete**: Rota DELETE `/products/{id}` que remove o produto com o ID correspondente da tabela de produtos.

### Funcionalidades Avançadas

- **Autenticação e Autorização**: Implementa autenticação via JWT para garantir que apenas usuários autenticados possam acessar as rotas de criação, atualização e exclusão. Implementa autorização baseada em roles (admin, user).
- **Validação de Dados**: Utiliza Pydantic para garantir que os dados recebidos nas requisições estejam no formato correto.
- **Paginação, Filtragem e Ordenação**: Adiciona paginação nas rotas de listagem para retornar um número limitado de produtos por página. Adiciona filtros para permitir busca por atributos específicos (ex: cor, preço). Implementa ordenação (ex: ordenar por preço, nome).
- **Manipulação de Transações**: Garante que as operações de criação, atualização e exclusão sejam transacionais.
- **Testes Unitários e de Integração**: Cria testes unitários para cada rota do CRUD e testes de integração para verificar a interação entre os componentes da API e o banco de dados.
- **Criação de Logs**: Implementa um sistema de logs para monitorar as operações CRUD realizadas.
- **Documentação Automática**: Utiliza as funcionalidades do FastAPI para gerar documentação automática da API utilizando Swagger ou Redoc.

## Configuração e Execução

### Pré-requisitos

- Python 3.8+
- Docker (opcional, para execução em containers)

### Configuração do Ambiente

1. Clone o repositório:

    ```bash
    git clone https://github.com/SEU_USUARIO/adventureworks-api.git
    cd adventureworks-api
    ```

2. Crie e ative um ambiente virtual:

    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
    ```

3. Instale as dependências:

    ```bash
    pip install -r requirements.txt
    ```

4. Configure as variáveis de ambiente:

    Crie um arquivo `.env` com as seguintes variáveis:

    ```env
    DATABASE_URL=postgresql://user:password@localhost/adventureworks
    SECRET_KEY=your_secret_key
    ALGORITHM=HS256
    ACCESS_TOKEN_EXPIRE_MINUTES=30
    ```

### Execução da Aplicação

1. Execute a aplicação:

    ```bash
    uvicorn main:app --reload
    ```

2. Acesse a documentação automática da API em [http://localhost:8000/docs](http://localhost:8000/docs).

### Execução com Docker

1. Construa a imagem Docker:

    ```bash
    docker build -t adventureworks-api .
    ```

2. Execute o container:

    ```bash
    docker run -d -p 8000:8000 --name adventureworks-api adventureworks-api
    ```

### Testes

1. Configure o ambiente de testes (utilizando SQLite em memória):

    No arquivo `.env`, configure a variável `DATABASE_URL` para `sqlite:///./test.db`.

2. Execute os testes:

    ```bash
    pytest --cov=./
    ```

3. Verifique o relatório de cobertura de testes:

    ```bash
    pytest --cov-report html
    ```

## Documentação

A documentação da API é gerada automaticamente pelo FastAPI e pode ser acessada em [http://localhost:8000/docs](http://localhost:8000/docs) ou [http://localhost:8000/redoc](http://localhost:8000/redoc).

## Considerações Finais

Este projeto visa proporcionar uma base sólida para desenvolver APIs RESTful utilizando o FastAPI, com foco em segurança, eficiência e manutenibilidade. Siga as melhores práticas de desenvolvimento e ajuste as configurações conforme necessário para o seu ambiente de produção.
