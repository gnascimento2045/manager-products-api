# Manager Products API

REST API for product and category management, built with NestJS, TypeORM and PostgreSQL.

> **Português:** This README is in English. For Portuguese version, see [LEIAME.md](./LEIAME.md)

## Tech Stack

- **Runtime:** Node.js
- **Framework:** NestJS
- **ORM:** TypeORM
- **Database:** PostgreSQL 16
- **Container:** Docker + Docker Compose
- **Docs:** Swagger / OpenAPI
- **Validation:** class-validator

## Prerequisites

- Node.js installed
- Docker and Docker Compose installed

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/gnascimento2045/manager-products-api.git
cd manager-products-api
```

### 2. Configure environment variables

```bash
cp .env.example .env
```

Edit `.env` with your values:

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASS=postgres
DB_NAME=manager-db
```

### 3. Start the database

```bash
docker compose up -d
```

### 4. Install dependencies

```bash
npm install
```

### 5. Start the server

```bash
npm run start:dev
```

API available at: `http://localhost:3000`  
Swagger docs at: `http://localhost:3000/api/docs`

## API Endpoints

### Categories

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /categories | List all categories |
| GET | /categories/:id | Get category by ID |
| POST | /categories | Create category |
| PUT | /categories/:id | Update category |
| DELETE | /categories/:id | Delete category |

### Products

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /products | List products (paginated) |
| GET | /products/:id | Get product by ID |
| POST | /products | Create product |
| PUT | /products/:id | Update product |
| DELETE | /products/:id | Delete product |

### Pagination

```
GET /products?page=1&limit=10
```

## Technical Decisions

### TypeORM
Chose TypeORM for its native integration with NestJS decorators and familiarity with the ActiveRecord/DataMapper pattern, which works well in medium-to-large projects.

### synchronize: true (dev only)
In development, TypeORM auto-syncs the schema with entities. In production this should be replaced with migrations.

### Docker Compose
PostgreSQL runs in a container to ensure environment consistency across machines without local database installation.

### Modular Architecture
Each domain (categories, products) has its own module, service, controller and DTOs, following NestJS best practices and making the codebase easy to scale.

## Frontend

The frontend was built with:
- **React 19** + Vite
- **TypeScript**
- **ANTD** - UI component library. Chose ANTD because I have experience with projects using it and found it more visually professional and easier to customize.

Repository: [manager-products-web](https://github.com/gnascimento2045/manager-products-web)

## Credits

This project was developed with assistance from AI (Claude - Anthropic) for:
- Initial project structure
- NestJS pattern suggestions
- TypeScript types review

All code was reviewed, understood and adapted manually.
