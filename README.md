# Our Relationship App — Backend

NestJS backend API for the Our Relationship App, built by Technology Rivers.

## Stack

- NestJS 10 (TypeScript)
- TypeORM + PostgreSQL
- Passport JWT authentication
- Swagger / OpenAPI docs
- Jest for unit and e2e tests

## Getting started

```bash
npm install
cp .env.example .env
```

Update `.env` with your local database credentials, then start Postgres (or run `docker compose up db`).

```bash
npm run start:dev
```

The API runs on `http://localhost:3000/api` by default. Swagger docs are available at `http://localhost:3000/api/docs`.

## Scripts

| Command | Description |
| --- | --- |
| `npm run start:dev` | Start in watch mode |
| `npm run build` | Compile to `dist/` |
| `npm run start:prod` | Run compiled build |
| `npm run lint` | Lint and auto-fix |
| `npm run test` | Unit tests |
| `npm run test:e2e` | End-to-end tests |
| `npm run migration:generate` | Generate a TypeORM migration |
| `npm run migration:run` | Run pending migrations |

## Project structure

```
src/
  auth/        JWT auth (login, strategy, guards)
  users/       User entity, DTOs, service, controller
  health/      Health check endpoint (Terminus)
  config/      Environment configuration and TypeORM data source
  common/      Shared filters and interceptors
  app.module.ts
  main.ts
test/          e2e tests
```

## Docker

```bash
docker compose up --build
```

Runs the API alongside a Postgres container.

## Notes

- Set `DB_SYNC=false` in any shared or production environment and use migrations instead.
- Rotate `JWT_SECRET` and store it outside of source control (e.g., a secrets manager) before deploying.
- If this project ever stores health-related or personal data covered by HIPAA, confirm BAA coverage for any third-party service (hosting, logging, email, etc.) before connecting it.
