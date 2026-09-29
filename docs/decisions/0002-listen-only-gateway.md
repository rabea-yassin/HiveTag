# 0002. The gateway only listens and never transmits power

- **Date:** 2026-09-29
- **Status:** Accepted
- **Source:** [PROJECT.md §2](../PROJECT.md#2-decisions-already-made)

## Context
Dedicated RF power transmitters (as in RFID) could feed the tags, but they add hardware, regulatory questions, and extra RF near the colonies.

## Decision
One gateway per apiary. It receives BLE advertisements only and never transmits power.

## Consequences
- Tags must survive on ambient energy alone.
- Minimal added RF exposure for the bees.
- The gateway is simple: a Pi or ESP32 running a BLE scanner.
