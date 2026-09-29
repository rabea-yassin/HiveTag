# 0007. Start with dev boards, USB powered and solder-free

- **Date:** 2026-09-29
- **Status:** Accepted

## Context
The owner is new to electronics. Debugging firmware, radio, sensors, and power at the same time on a custom board would be very hard.

## Decision
Prototype with a Seeed XIAO nRF52840 and an Adafruit SHT40 (STEMMA QT), powered by USB, and avoid soldering where possible.

## Consequences
- One hard problem at a time. Energy work starts only after the data path works end to end.
- Dev-board parasitics limit power measurements. The true numbers come with the custom PCB.
