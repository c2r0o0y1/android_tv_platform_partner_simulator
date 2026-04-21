# FireTV Partner Platform Simulator

Lightweight monorepo for building a Fire TV partner simulation stack with an Android TV launcher and a FastAPI backend.

## Repo Overview

- `android-tv-launcher/` - Android TV app foundation (Kotlin + Gradle, terminal-first workflow)
- `backend/` - FastAPI service, PostgreSQL integration, Docker setup
- `docs/` - architecture notes, API contracts, and ADRs

## Phase 1 Setup (macOS, no Android Studio required)

### 1) Clone and enter repository

```bash
git clone <your-repo-url>
cd AndTvSimulator
```

### 2) Backend quick start

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
cp .env.example .env
uvicorn app.main:app --reload --port 8000
```

Health check:

```bash
curl http://127.0.0.1:8000/health
```

### 3) Backend with Docker Compose (API + PostgreSQL)

```bash
cd backend
cp .env.example .env
docker compose up --build
```

### 4) Android CLI setup (SDK + Gradle + Kotlin)

Use the full command list in `android-tv-launcher/README.md` and `docs/macos-android-cli-setup.md`.

Build from terminal:

```bash
cd android-tv-launcher
gradle :app:assembleDebug
```

Install on emulator/device:

```bash
gradle :app:installDebug
```

Optional wrapper setup after Gradle is installed:

```bash
cd android-tv-launcher
gradle wrapper
./gradlew :app:assembleDebug
```

## Planned Phases

- **Phase 1 (current):** Monorepo foundation, backend skeleton, Android TV skeleton, docs, CLI setup
- **Phase 2:** Partner configuration ingestion, basic content rail APIs, app data binding, initial telemetry events
- **Phase 3:** Diagnostics tooling, contract validation, richer test coverage, CI workflows
