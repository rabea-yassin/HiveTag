# Backend

The ingest API, data model, and later the auth, claiming, groups, and alerts.

- **Active from:** Phase 0 (skeleton with `/health`, `rf_survey` table)
- **Stack:** Python 3.11+, FastAPI, SQLAlchemy 2, Alembic, PostgreSQL + TimescaleDB, pytest
- **Contract:** ingest API in [docs/protocol.md §2](../docs/protocol.md#2-gateway--backend-api)
