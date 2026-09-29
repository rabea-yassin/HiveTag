# HiveTag protocol

The contract shared by the tag firmware, gateway, tools, and backend. Any change bumps the protocol version, and this file is updated **before** any code.

## 1. BLE advertisement packet (protocol v1)

Advertisement type: non-connectable, undirected. AD structures: Flags (3 bytes) + Manufacturer Specific Data.

Manufacturer Specific Data payload (little-endian):

| Offset | Size | Field | Notes |
|--------|------|-------|-------|
| 0 | 2 | Company ID | `0xFFFF` (reserved for testing; fine for prototypes, not for a product) |
| 2 | 1 | Magic | `0xBE` identifies HiveTag packets |
| 3 | 1 | Protocol version | `0x01` |
| 4 | 6 | Tag ID | lower 48 bits of the nRF FICR DEVICEID |
| 10 | 2 | Seq | uint16. Duty-cycled mode: increments per measurement. Intermittent mode: random per wake-up. Used for deduplication. |
| 12 | 2 | Temperature | int16, units of 0.01 °C |
| 14 | 2 | Humidity | uint16, units of 0.01 %RH |
| 16 | 2 | Storage voltage | uint16, mV (capacitor/supercap) at measurement time |
| 18 | 1 | Flags | bit0 = first packet after boot (duty-cycled mode); bit1 = sensor error; bit2 = low energy; bit3 = intermittent mode; others reserved |

Total manufacturer data: 19 bytes (fits within the 31-byte legacy advertisement).

**Rules**

- Each measurement is broadcast as a short burst (e.g., 2–5 advertisements) with the same seq; the gateway deduplicates.
- Duty-cycled mode: seq resets after a brownout; bit0 marks a new session, not packet loss.
- Intermittent mode (bit3): packet loss cannot be computed from seq. Instead, the time between receptions is itself a measurement of harvested energy (shorter interval = more energy).
- v2 (later): add a 4-byte truncated HMAC with a per-tag key to prevent spoofing.

## 2. Gateway → backend API

`POST /api/v1/ingest` — header `X-Gateway-Key: <key>`

```json
{
  "gateway_id": "gw-batuf-01",
  "sent_at": "2026-09-27T10:00:00Z",
  "readings": [
    {
      "tag_id": "a1b2c3d4e5f6",
      "seq": 1042,
      "temperature_c": 34.62,
      "humidity_pct": 58.10,
      "storage_mv": 3120,
      "flags": 0,
      "rssi": -71,
      "received_at": "2026-09-27T09:59:41Z"
    }
  ]
}
```

`POST /api/v1/gateways/{id}/heartbeat` — uptime, buffered count, software version.
