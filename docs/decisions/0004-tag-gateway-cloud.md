# 0004. Data flows tag → gateway → cloud, never tag → cellular

- **Date:** 2026-09-29
- **Status:** Accepted

## Context
Direct cellular (NB-IoT, LTE-M) from each tag would remove the gateway, but a cellular transmission needs orders of magnitude more energy than harvesting provides.

## Decision
Tags only talk to a local gateway, and the gateway uploads to the backend.

## Consequences
- A gateway is required at every apiary.
- The gateway must buffer offline (SQLite) and upload in batches.
