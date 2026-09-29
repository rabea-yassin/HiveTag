# 0008. Firmware supports duty-cycled and intermittent power modes

- **Date:** 2026-09-29
- **Status:** Accepted
- **Source:** [PROJECT.md §2](../PROJECT.md#2-decisions-already-made)

## Context
Development, USB, solar, and supercap setups benefit from a normal sleep/wake cycle with a sequence counter. Ambient harvesting needs harvest-then-fire (ADR 0005).

## Decision
The firmware has two modes: duty-cycled and intermittent. Packets say which mode they come from (flags bit3).

## Consequences
- The gateway, backend, and dashboards must handle both modes everywhere: dedup, packet loss, stale detection, and energy health.
- The simulator in tools/ must generate both.
