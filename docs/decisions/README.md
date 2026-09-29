# Decisions

Architecture decision records (ADRs): one short file per decision, explaining **why**. Decisions are never deleted. When one changes, a new ADR supersedes it.

To add one: copy [TEMPLATE.md](TEMPLATE.md) to `NNNN-short-title.md` with the next number, and add it to the index below.

| # | Decision | Status |
|---|----------|--------|
| [0001](0001-ambient-rf-primary-energy.md) | Ambient RF is the primary energy goal; solar is the fallback | Accepted |
| [0002](0002-listen-only-gateway.md) | The gateway only listens and never transmits power | Accepted |
| [0003](0003-ble-advertisements-only.md) | Tags broadcast readings as BLE advertisements | Accepted |
| [0004](0004-tag-gateway-cloud.md) | Data flows tag → gateway → cloud | Accepted |
| [0005](0005-intermittent-harvest-then-fire.md) | Ambient-powered tags use harvest-then-fire | Accepted |
| [0006](0006-nfc-claiming.md) | Tags are claimed with a passive NFC sticker | Accepted |
| [0007](0007-dev-boards-first.md) | Start with dev boards, USB powered and solder-free | Accepted |
| [0008](0008-dual-power-modes.md) | Firmware supports two power modes | Accepted |
