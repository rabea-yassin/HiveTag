# HiveTag

**Battery-free beehive sensors powered by invisible energy.**

HiveTag is a small sensor tag that sits inside a beehive and reports the brood nest's temperature and humidity over Bluetooth Low Energy, **with no battery**. The goal is to power it from energy that is already there: ambient radio waves (cellular, Wi-Fi) and the colony's own body heat. Solar is kept only as a fallback. A listen-only gateway at the apiary collects the broadcasts and forwards them to a backend and dashboard, so a beekeeper can spot a weak, queenless, or stressed colony without opening every hive.

This is a learning-in-public project: an electronics and energy-harvesting journey by a software engineer. Every design decision and every measurement is written down in this repo.

> Status: **Phase 0** (setup, learning, RF site survey). Progress is slower during the university semester.

## How it works

```
 [Tag in hive] --BLE advertisement--> [Gateway at apiary] --HTTPS--> [Backend] <--> [Dashboard]
      ^                                (listen-only,                  (FastAPI,        (Grafana now,
      | ambient RF and/or colony heat   buffers offline)               TimescaleDB)     web app later)
      | (solar as fallback) + capacitor
```

- **Tag:** nRF52840 + SHT40 sensor. It broadcasts readings as BLE advertisements, with no connections. For ambient power it runs in "harvest-then-fire" mode: a capacitor charges, the MCU wakes, it measures and transmits once, then it powers off.
- **Gateway:** a laptop, later a Raspberry Pi or ESP32. It only listens and never transmits power.
- **Backend:** FastAPI + PostgreSQL/TimescaleDB, with Grafana for early dashboards.

## Repository map

| Path | What's there |
|------|--------------|
| [docs/protocol.md](docs/protocol.md) | BLE packet format and ingest API: the contract between all components |
| [docs/decisions/](docs/decisions/) | Architecture decision records: why things are the way they are |
| [docs/experiments/](docs/experiments/) | Dated experiment logs: RF survey, power, range, field results |
| [firmware/tag/](firmware/tag/) | Tag firmware (nRF Connect SDK / Zephyr) |
| [gateway/](gateway/) | BLE scanner + uploader (Python) |
| [backend/](backend/) | Ingest API and data model (FastAPI) |
| [dashboard/](dashboard/) | Grafana provisioning |
| [web/](web/) | Web app (later) |
| [hardware/](hardware/) | KiCad projects, BOMs, enclosures |
| [tools/](tools/) | Packet decoder, tag simulator, RF survey helper |

## Roadmap

| Phase | Goal | Done when |
|-------|------|-----------|
| 0 | Setup, learning, RF site survey | Simulated packets in Grafana, and a measured answer to "how much RF is at the apiary?" |
| 1 | End-to-end MVP, USB powered | A real reading from the tag appears on a chart |
| 2 | Energy per reading | Energy per reading measured; tag runs from a capacitor |
| 3 | Battery-free on harvested energy | 7+ days on harvested energy alone |
| 4 | Field pilot + real platform | Beekeeper taps a tag, sees hives, gets alerts |
| 5–7 | Custom PCBs: matchbox → coin → sticker | |

Tasks and progress: [GitHub Issues](https://github.com/rabea-yassin/HiveTag/issues) and [milestones](https://github.com/rabea-yassin/HiveTag/milestones).

## Next step

1. Order the Phase 0 parts ([#1](https://github.com/rabea-yassin/HiveTag/issues/1)).
2. While waiting for them: start the soldering practice kit and learn the multimeter, and install the nRF Connect SDK.
3. Platform: write the v1 packet decoder and tag simulator in `tools/`, with tests.
