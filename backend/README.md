# Backend

The ingest API, data model, and later the auth, claiming, groups, and alerts.

- **Active from:** Phase 0 (skeleton with `/health`, `rf_survey` table)
- **Stack:** Python 3.11+, FastAPI, SQLAlchemy 2, Alembic, PostgreSQL + TimescaleDB, pytest
- **Specs:** ingest API [§4.2](../docs/PROJECT.md#42-gateway--backend-api), data model [§4.3](../docs/PROJECT.md#43-data-model-initial), health rules [§4.5](../docs/PROJECT.md#45-health-and-status-rules)
