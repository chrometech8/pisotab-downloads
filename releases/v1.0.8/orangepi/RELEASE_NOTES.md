# OrangePi Image Release `edge-image-v1.0.8`

Release date: 2026-04-08

## What’s Fixed
- Correct production `EDGE_SHARED_SECRET` baked into the image
- Prevents `401 Unauthorized` during portal activation machine-ID verification
- Keeps the latest coin-reading accuracy hardening and relay timing updates

## Included Runtime Defaults
- `COIN_LINE=12`
- `GATE_LINE=11`
- `GATE_SYSFS_GPIO=11`
- `GATE_ACTIVE_HIGH=1`
- `COIN_GAP_MS=160`
- `COIN_SAFE_MIN_GAP_MS=420`
- `GATE_BETWEEN_COINS_MS=120`
- `GATE_SAFE_MIN_BETWEEN_COINS_MS=220`

## Clean Image Notes
- Database state removed
- Machine identity reset for fresh deployment
- Writable `edgeapp` data directory preserved for first boot

## Assets
- `chrometech-edge-v1.0.8.img.xz`
- `chrometech-edge-v1.0.8.img.xz.sha256`

## Flashing
1. Open Balena Etcher
2. Select `chrometech-edge-v1.0.8.img.xz`
3. Select target microSD card
4. Flash and boot the OrangePi

## Verification
```bash
sha256sum -c chrometech-edge-v1.0.8.img.xz.sha256
```
