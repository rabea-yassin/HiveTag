# 0001. Ambient RF is the primary energy goal; solar is the fallback

- **Date:** 2026-09-29
- **Status:** Accepted

## Context
The point of the project is a tag powered by invisible energy. Ambient RF from cellular and Wi-Fi is everywhere near the apiary, but at borderline levels. Colony heat gives a steady temperature difference. Solar is reliable but visible and bulky.

## Decision
Pursue ambient RF harvesting as the primary energy source, possibly combined with thermoelectric harvesting from colony heat. Solar is the fallback and the development aid. The final choice depends on the Phase 0 RF site survey.

## Consequences
- The RF site survey ([#6](https://github.com/rabea-yassin/HiveTag/issues/6)) is a blocking experiment for Phase 3.
- Every power claim must be backed by a logged measurement.
- If the survey shows too little RF, this decision will be superseded by a thermoelectric, hybrid, or solar ADR.
