# OrangePi Image Release `edge-image-v1.0.9`

Release date: 2026-04-09

## What’s Included
- Synced from live Orange Pi backend (`192.168.1.18`) application payload under `/opt/chrometech-edge`
- Synced live `/etc/chrometech/chrometech-edge.env` including working production `EDGE_SHARED_SECRET`
- Coin/relay timing profile carried from live robust backend (`COIN_GAP_MS=175`, `COIN_SAFE_MIN_GAP_MS=260`, `COIN_MIN_EDGE_GAP_MS=6`, `GATE_BETWEEN_COINS_MS=100`, `GATE_SAFE_MIN_BETWEEN_COINS_MS=160`)

## Clean Production State
- Removed edge runtime DB artifacts (`edge.db`, `-wal`, `-shm`)
- Reset machine identity (`/etc/machine-id` cleared, `/var/lib/dbus/machine-id` removed)
- Preserved writable edge data directory permissions for first boot

## Assets
- `chrometech-edge-v1.0.9.img.xz`
- `chrometech-edge-v1.0.9.img.xz.sha256`

## Integrity
```bash
sha256sum -c chrometech-edge-v1.0.9.img.xz.sha256
```

## Flashing
1. Open Balena Etcher
2. Select `chrometech-edge-v1.0.9.img.xz`
3. Select target microSD card
4. Flash and boot Orange Pi
