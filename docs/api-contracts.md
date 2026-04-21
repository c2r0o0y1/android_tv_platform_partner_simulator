# API Contracts (Phase 1)

## Health Check

- **Method:** `GET`
- **Path:** `/health`
- **Purpose:** Basic availability and startup sanity check.

### Success Response (200)

```json
{
  "status": "ok",
  "service": "firetv-partner-platform-simulator-api",
  "environment": "dev"
}
```

## Future Contract Areas (Phase 2+)

- Partner registration and config ingestion
- Content rails retrieval
- Telemetry ingestion endpoints
- Diagnostics and run-state endpoints
