---
name: backend-api-nodejs
description: "Generate a Node.js (Express) backend API with Swagger/OpenAPI documentation. Use for: REST APIs, backend scaffolds, CRUD endpoints, in-memory or PostgreSQL storage. Triggers: build a backend API, generate Express endpoints, backend with Swagger, Node.js API, create endpoints, REST API."
---

# Backend API Generator — Node.js (Contract-Driven, Swagger-First)

This skill generates **runnable backend APIs** using **Node.js (Express)** with **Swagger / OpenAPI documentation**.

Behavior and complexity are strictly controlled by the user prompt. The skill does not assume databases, infrastructure, or complexity — those are introduced **only when explicitly requested**.

## Table of Contents

1. [When to Use](#when-to-use)
2. [Clarification Questions](#clarification-questions)
3. [Storage Rules](#storage-rules)
4. [Architecture Rules](#architecture-rules)
5. [API & Swagger Rules](#api--swagger-rules)
6. [Placeholder Rules](#placeholder-rules)
7. [Output Requirements](#output-requirements)
8. [Governing Contracts](#governing-contracts)

---

## When to Use

Use this skill when the user:
- Wants a backend API
- Needs Swagger / OpenAPI documentation
- Wants a clean, safe backend scaffold
- Is prototyping or building real systems

Triggering phrases include: "Build a backend API", "Generate Express endpoints", "Backend with Swagger", "Node.js API", "create REST endpoints", "backend service".

---

## Clarification Questions

Ask questions **only when required to proceed**:

1. **Storage type?** — in-memory (default) or PostgreSQL
2. **Entities / resources?** — what data models are needed
3. **Required operations per entity?** — create, list, get, update, delete
4. **Placeholder allowance?** — for complex logic that can't be fully implemented

If the prompt is sufficient, **do not ask questions**.

---

## Storage Rules

### In-Memory Mode (Default)

Use in-memory storage when the prompt does not mention a database or the user is prototyping:
- Use Maps or arrays
- Treat storage as ephemeral
- No persistence assumptions

### PostgreSQL Mode

Use PostgreSQL **only when explicitly requested**:
- Use `DATABASE_URL` from environment variables
- Use migrations for all schema changes
- Follow database and migration contracts strictly

---

## Architecture Rules

Even in simple or single-file setups, these boundaries must be respected conceptually:

- **Routes / Controllers** — thin, no business logic
- **Services** — contain all business logic
- **Repositories** — handle all persistence
- No layer skipping allowed

---

## API & Swagger Rules

- Swagger is **mandatory** for all endpoints — accessible via `/docs`
- Every route must be documented
- Request and response schemas must be explicit
- Error responses must be documented for all failure cases

---

## Placeholder Rules

When the prompt allows placeholders:
- Define stable interfaces that won't change
- Return deterministic, realistic data
- Document all placeholders clearly in Swagger and README

---

## Output Requirements

The generated backend must:

- Run via `node index.js` or equivalent
- Expose Swagger UI at `/docs`
- Include `.env.example` if any configuration is used
- Include database migrations when PostgreSQL is used
- Include a README with setup instructions, env vars, and endpoint summary

---

## Governing Contracts

This skill enforces the following principles (contracts override this file if conflicts arise):

- **Architecture** — clean separation of routes, services, repositories
- **Database** — safe query patterns, no raw string interpolation, parameterized queries
- **Configuration** — all secrets via environment variables, never hardcoded
- **Migrations** — versioned, reproducible, never destructive by default
- **Code Quality** — clarity over cleverness, no premature optimization
- **Placeholders** — stable interfaces, documented, deterministic
- **Swagger** — complete, accurate, every endpoint covered
- **README** — setup steps, env vars, how to run, how to test

---

## Notes

- Do not add features not explicitly requested
- Do not introduce infrastructure implicitly
- Do not optimize prematurely
- Prefer clarity over cleverness
- This skill exists to build backends that **can grow safely without forcing complexity**