# Tag firmware

nRF Connect SDK (Zephyr) application for the HiveTag sensor tag. It reads the SHT40 and broadcasts protocol v1 advertisements ([docs/protocol.md](../../docs/protocol.md)).

- **Active from:** Phase 0 (blinky, SHT40 over USB) → Phase 1 (v1 packets, duty-cycled) → Phase 2 (intermittent mode)
- **Board:** Seeed XIAO nRF52840, target `xiao_ble` (check the name in the installed SDK)
- **Power modes:** duty-cycled and intermittent ([ADR 0008](../../docs/decisions/0008-dual-power-modes.md))
- **Rule:** energy per reading is first class: no busy-waiting, no unneeded peripherals, no logging in low-power builds.

## Build and flash
*(to be filled in when the first app exists)*

Flashing via UF2: double-tap reset, then copy `build/zephyr/zephyr.uf2` to the USB drive that appears.
