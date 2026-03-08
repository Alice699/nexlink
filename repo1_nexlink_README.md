<div align="center">

# ⚡ NexLink

**A blazing-fast URL shortener with real-time analytics**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?style=flat-square&logo=postgresql&logoColor=white)](https://postgresql.org)
[![Redis](https://img.shields.io/badge/Redis-7-DC382D?style=flat-square&logo=redis&logoColor=white)](https://redis.io)
[![Docker](https://img.shields.io/badge/Docker-ready-2496ED?style=flat-square&logo=docker&logoColor=white)](https://docker.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

*Shorten. Track. Optimize.*

</div>

---

## Overview

NexLink is a production-ready URL shortener built with a modern Python backend and React frontend. It provides real-time click analytics, custom aliases, expiration dates, QR code generation, and a clean dashboard to monitor your links.

Built as a full-stack learning project to demonstrate REST API design, async Python, and React state management.

## Features

- **URL Shortening** — Generate short links in milliseconds
- **Custom Aliases** — Choose your own slug (e.g. `nex.link/my-project`)
- **Analytics Dashboard** — Track clicks, referrers, geographic data, and devices
- **QR Code Generation** — Auto-generate QR codes for every link
- **Link Expiration** — Set TTL for temporary links
- **Rate Limiting** — Redis-backed rate limiting per IP
- **API-first** — Full REST API with OpenAPI docs at `/docs`

## Tech Stack

**Backend**
- [FastAPI](https://fastapi.tiangolo.com) — Async Python web framework
- [SQLAlchemy](https://sqlalchemy.org) — ORM with async support
- [PostgreSQL](https://postgresql.org) — Primary database
- [Redis](https://redis.io) — Caching & rate limiting
- [Alembic](https://alembic.sqlalchemy.org) — Database migrations

**Frontend**
- [React 18](https://react.dev) — UI library
- [TanStack Query](https://tanstack.com/query) — Server state management
- [Recharts](https://recharts.org) — Analytics charts
- [Tailwind CSS](https://tailwindcss.com) — Styling

**DevOps**
- Docker & Docker Compose
- GitHub Actions CI/CD

## Project Structure

```
nexlink/
├── backend/
│   ├── app/
│   │   ├── api/          # Route handlers
│   │   ├── core/         # Config, security, dependencies
│   │   ├── models/       # SQLAlchemy models
│   │   ├── schemas/      # Pydantic schemas
│   │   └── services/     # Business logic
│   ├── alembic/          # DB migrations
│   └── tests/            # Pytest test suite
├── frontend/
│   ├── src/
│   │   ├── components/   # Reusable UI components
│   │   ├── pages/        # Page components
│   │   ├── hooks/        # Custom React hooks
│   │   └── lib/          # API client, utils
│   └── public/
├── docker-compose.yml
└── Makefile
```

## Getting Started

**Prerequisites:** Docker & Docker Compose installed

```bash
# Clone the repo
git clone https://github.com/Alice699/nexlink.git
cd nexlink

# Copy environment variables
cp .env.example .env

# Start all services
docker compose up -d

# Run database migrations
docker compose exec backend alembic upgrade head
```

App will be running at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- API Docs: http://localhost:8000/docs

**Local Development (without Docker)**

```bash
# Backend
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload

# Frontend (new terminal)
cd frontend
npm install
npm run dev
```

## API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/v1/links` | Create short link |
| `GET` | `/api/v1/links` | List all links |
| `GET` | `/api/v1/links/{id}` | Get link details |
| `DELETE` | `/api/v1/links/{id}` | Delete link |
| `GET` | `/api/v1/links/{id}/analytics` | Get click analytics |
| `GET` | `/{slug}` | Redirect to original URL |

## Running Tests

```bash
cd backend
pytest tests/ -v --cov=app --cov-report=term-missing
```

## Roadmap

- [ ] User authentication & multi-user support
- [ ] Team workspaces
- [ ] Webhook support on click events
- [ ] Link password protection
- [ ] CSV export for analytics

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](LICENSE) © Robbian Saputra Gumay
