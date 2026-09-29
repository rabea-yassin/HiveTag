# Gateway

A Python listen-only BLE scanner and uploader ([ADR 0002](../docs/decisions/0002-listen-only-gateway.md)). It scans continuously and filters HiveTag packets (company `0xFFFF`, magic `0xBE`). It decodes and deduplicates `(tag_id, seq)`, attaches RSSI and a receive timestamp, buffers to SQLite when offline, and batch-uploads to `POST /api/v1/ingest` ([docs/protocol.md §2](../docs/protocol.md#2-gateway--backend-api)).

- **Active from:** Phase 1 (laptop), Phase 4 (Raspberry Pi / ESP32 in the field)
- **Stack:** Python 3.11+, bleak, httpx, pydantic, pytest
