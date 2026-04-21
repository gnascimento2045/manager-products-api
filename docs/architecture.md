# Architecture Diagram

```mermaid
┌─────────────────────────────────────────────────────┐
│                    CLIENT (React)                   │
│                  localhost:5173                      │
└─────────────────────┬───────────────────────────────┘
                      │ HTTP REST
                      ▼
┌─────────────────────────────────────────────────────┐
│               NestJS API (Node.js)                  │
│                  localhost:3000                     │
│                                                     │
│  ┌─────────────────┐     ┌─────────────────────┐   │
│  │ CategoriesModule│     │   ProductsModule     │   │
│  │                 │     │                      │   │
│  │ POST /categories│     │ POST   /products     │   │
│  │ GET  /categories│     │ GET    /products     │   │
│  │ GET  /categories│     │ GET    /products/:id │   │
│  │       /:id      │     │ PUT    /products/:id │   │
│  │ DEL  /categories│     │ DELETE /products/:id │   │
│  │       /:id      │     │                      │   │
│  └────────┬────────┘     └──────────┬──────────┘   │
│           │                         │               │
│           └────────────┬────────────┘               │
│                        │ TypeORM                    │
└────────────────────────┼────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│              PostgreSQL (Docker)                    │
│                  localhost:5432                    │
│                                                     │
│   ┌──────────────┐        ┌──────────────────┐     │
│   │  categories  │        │     products     │     │
│   │──────────────│        │──────────────────│     │
│   │ id (uuid) PK │◄───────│ id (uuid) PK     │     │
│   │ name         │        │ name             │     │
│   │ description  │        │ description      │     │
│   └──────────────┘        │ price            │     │
│                           │ isActive         │     │
│                           │ category_id FK   │     │
│                           └──────────────────┘     │
└─────────────────────────────────────────────────────┘
```
