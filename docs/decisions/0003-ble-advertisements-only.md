# 0003. Tags broadcast readings as BLE advertisements, with no connections

- **Date:** 2026-09-29
- **Status:** Accepted
- **Source:** [PROJECT.md §2](../PROJECT.md#2-decisions-already-made)

## Context
A BLE connection needs a handshake, stays awake longer, and costs much more energy per reading than a single broadcast.

## Decision
Tags send non-connectable advertisements carrying the reading (packet format in PROJECT.md §4.1). There are no connections.

## Consequences
- Lowest energy per reading. Any gateway or phone can receive the data.
- There are no acknowledgements, so each reading is sent as a short burst and the gateway deduplicates.
- Anyone can read or spoof packets. Authentication is planned for protocol v2.
