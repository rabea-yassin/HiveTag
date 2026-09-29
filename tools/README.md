# Tools

Utilities shared across the project:

- **Packet decoder:** parses protocol v1 manufacturer data ([PROJECT.md §4.1](../docs/PROJECT.md#41-ble-advertisement-packet-protocol-v1)).
- **Tag simulator:** generates realistic packets in both power modes, so the backend and dashboard can be built before hardware exists.
- **RF survey helper:** enters or imports survey measurements into `rf_survey`.

- **Active from:** Phase 0
- **Stack:** Python 3.11+, pydantic, pytest
