# 0005. Ambient-powered tags use intermittent harvest-then-fire operation

- **Date:** 2026-09-29
- **Status:** Accepted

## Context
Ambient RF delivers about 1 µW or less. A sleeping MCU with a running timer already uses several µW, so a normal sleep/wake cycle would never break even.

## Decision
The MCU is fully off. A capacitor charges, and a voltage supervisor powers the MCU when a threshold is reached. The MCU measures and transmits once, then power drops again.

## Consequences
- No sleep current: all harvested energy goes into readings.
- The reading rate adjusts itself to the available energy, and the interval between receptions becomes a measure of harvested energy.
- There is no persistent state between wake-ups. Seq is random per wake-up, and packet loss cannot be computed.
- Energy per reading (boot + sensor + BLE burst) must be minimized (Phase 2).
