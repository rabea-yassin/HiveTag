# 0006. Tags are claimed by tapping a passive NFC sticker

- **Date:** 2026-09-29
- **Status:** Accepted
- **Source:** [PROJECT.md §2](../PROJECT.md#2-decisions-already-made)

## Context
A beekeeper needs a simple way to link a physical tag to their account. The tag has almost no energy and no user interface.

## Decision
Each tag carries a passive NFC sticker (NTAG213/215) that encodes a claim URL, with a printed QR code as a fallback.

## Consequences
- Works with zero tag power, on iPhone and Android, without a native app.
- The backend needs a /claim/{tag_id} flow (PROJECT.md §4.4).
