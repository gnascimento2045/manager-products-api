# Manager Products API

API REST para gerenciamento de produtos e categorias, construída com NestJS, TypeORM e PostgreSQL.

## Tecnologias

- **Runtime:** Node.js
- **Framework:** NestJS
- **ORM:** TypeORM
- **Banco de dados:** PostgreSQL 16
- **Container:** Docker + Docker Compose
- **Documentação:** Swagger / OpenAPI
- **Validação:** class-validator

## Pré-requisitos

- Node.js instalado
- Docker e Docker Compose instalados

## Começando

### 1. Clonar o repositório

```bash
git clone https://github.com/gnascimento2045/manager-products-api.git
cd manager-products-api
```

### 2. Configurar variáveis de ambiente

```bash
cp .env.example .env
```

Edite o `.env` com suas configurações:

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASS=postgres
DB_NAME=manager-db
```

### 3. Iniciar o banco de dados

```bash
docker compose up -d
```

### 4. Instalar dependências

```bash
npm install
```

### 5. Iniciar o servidor

```bash
npm run start:dev
```

API disponível em: `http://localhost:3000`  
Documentação Swagger: `http://localhost:3000/api/docs`

## Endpoints da API

### Categorias

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | /categories | Listar todas as categorias |
| GET | /categories/:id | Buscar categoria por ID |
| POST | /categories | Criar categoria |
| PUT | /categories/:id | Atualizar categoria |
| DELETE | /categories/:id | Deletar categoria |

### Produtos

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | /products | Listar produtos (paginado) |
| GET | /products/:id | Buscar produto por ID |
| POST | /products | Criar produto |
| PUT | /products/:id | Atualizar produto |
| DELETE | /products/:id | Deletar produto |

### Paginação

```
GET /products?page=1&limit=10
```

## Decisões Técnicas

### TypeORM
Escolhi o TypeORM pela integração nativa com decorators do NestJS e pela familiaridade com o padrão ActiveRecord/DataMapper, que funciona bem em projetos de médio/grande porte.

### synchronize: true (dev only)
Em desenvolvimento, o TypeORM sincroniza o schema automaticamente com as entidades. Em produção isso deve ser substituído por migrations.

### Docker Compose
O PostgreSQL roda em container para garantir consistência de ambiente entre máquinas sem precisar instalar banco local.

### Arquitetura Modular
Cada domínio (categorias, produtos) tem seu próprio módulo, service, controller e DTOs, seguindo as melhores práticas do NestJS e facilitando a escalabilidade.

## Frontend

O frontend foi construído com:
- **React 19** + Vite
- **TypeScript**
- **ANTD** - biblioteca de componentes UI. Escolhi o ANTD porque tenho experiência em projetos que usam e achei a aparência mais profissional e fácil de customizar.

Repositório: `manager-products-web`

## Créditos

Esse projeto foi desenvolvido com ajuda de IA (Claude - Anthropic) para:
- Estrutura inicial do projeto
- Sugestões de padrões NestJS
- Revisão de tipos TypeScript

Todo código foi revisado, entendido e adaptado manualmente.
