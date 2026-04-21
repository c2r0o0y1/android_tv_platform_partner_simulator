# ADR-001: Initial Stack Selection

## Status
Accepted

## Context
Need a lightweight, recruiter-friendly setup that runs on macOS with limited storage and avoids heavy IDE requirements.

## Decision
- Android app: Kotlin + Gradle, XML-based UI, Android TV-focused manifest and activities.
- Backend: FastAPI + SQLAlchemy + PostgreSQL.
- Local infra: Docker Compose for API + PostgreSQL.
- Tooling: VS Code + terminal workflow.

## Rationale
- Keeps setup and disk usage lower than full Android Studio workflows.
- FastAPI provides fast iteration for service APIs.
- Docker Compose gives predictable local DB setup.
- XML layouts reduce complexity versus early Compose for TV adoption in a terminal-first foundation.

## Consequences
- Emulator/device provisioning is manual via Android SDK CLI tools.
- UI development is code-driven instead of visual designer-driven.
- Phase 2 can still migrate selected surfaces to Compose when justified.
