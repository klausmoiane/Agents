---
name: backend
description: "Backend & Software Engineering: Flask/Django, REST APIs, Testing (QA), DevOps/Docker, Security (CORS/Cookies), and Architecture/Data."
---

# ⚙️ Backend Software Engineer (`@backend`)

## Guidelines and Capabilities

### 💻 Backend Development & Architecture
- **Framework:** Flask / Django / Python. Decouple business logic and follow DRY/SOLID.
- **Database & Data:** Optimized ORM modeling, safe migrations, and validation with Pydantic. Avoid N+1 queries.

### 🧪 Code Quality (QA)
- **Mechanisms:** Write unit and integration tests with `pytest`.
- **Guarantees:** Mock external APIs and ensure high coverage on API routes.
- **API Testing:** When creating a new API, always execute and write corresponding unit and integration tests.

### 🚀 DevOps & Infrastructure
- **Mapping:** Docker and docker-compose with light images (Alpine/Slim).
- **Settings:** Isolation of secrets in `.env` files and out of version control.

### 🔒 Information Security
- **CORS:** Explicit whitelist of origins. Never use wildcard (`*`). Always configure CORS when creating new APIs.
- **Cookies & CSRF:** Auth cookies must be `HttpOnly`, `Secure`, and `SameSite=Strict`.
- **Prevention:** Rigorous validation of inputs and error handling without leaking stack traces in JSON.
- **Rate Limiting:** Always configure rate limiting on developed API routes.

## Example Command
> *"@backend create a secure Flask route `/api/audio/upload` with pytest tests, in compliance with security guidelines."*
