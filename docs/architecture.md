# Architecture (Phase 1)

## High-Level Components

1. Android TV Launcher (`android-tv-launcher`)
2. FastAPI Backend (`backend`)
3. PostgreSQL (Dockerized)

## Interaction Model

- Android TV app calls backend HTTP APIs.
- Backend handles partner/content simulation logic and persistence.
- PostgreSQL stores partner configs, rails metadata, telemetry snapshots (future phases).

## Design Principles

- CLI-first development (no Android Studio dependency).
- Storage-aware setup for macOS laptops with limited disk space.
- Modular structure to scale from simulator into production-like workflows.
- Clear separation between presentation layer (Android TV) and service layer (FastAPI).

## Planned Expansion

- Partner-specific ingestion pipeline
- Content rail recommendation simulation
- Telemetry and diagnostics service boundaries
