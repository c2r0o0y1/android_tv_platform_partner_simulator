# Backend (FastAPI)

## What this contains

- FastAPI app scaffold
- Health endpoint (`GET /health`)
- SQLAlchemy session/base setup for PostgreSQL
- Docker setup for API + PostgreSQL

## 1) Local macOS setup (without Docker)

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
cp .env.example .env
uvicorn app.main:app --reload --port 8000
```

Verify:

```bash
curl http://127.0.0.1:8000/health
```

## 2) Run with Docker Compose (API + PostgreSQL)

```bash
cd backend
cp .env.example .env
docker compose up --build
```

Verify:

```bash
curl http://127.0.0.1:8000/health
```

## 3) Stop containers

```bash
docker compose down
```
