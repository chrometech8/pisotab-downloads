# OrangePi Image Release `edge-image-v1.0.7`

Release date: 2026-04-07

## What’s Included
- Updated CHROMETECH PisoTAB OrangePi backend image
- Coin-reading accuracy hardening for multi-pulse coins
- Short relay-off reader-busy window between accepted coins
- Reader status fields exposed for Hub/Client UI feedback
- GPIO relay startup export for `gpio11` / physical pin 5

## Clean Image Notes
- Packaged databases removed
- Machine identity reset for fresh deployment
- `edgeapp` writable data directory preserved for first boot
- No baked admin static token carried into the image

## Assets
- `chrometech-edge-v1.0.7.img.xz`
- `chrometech-edge-v1.0.7.img.xz.sha256`

## Compatibility
- Intended for current Android Hub/Client releases
- Verified backend pin/runtime defaults:
  - `COIN_LINE=12`
  - `GATE_LINE=11`
  - `GATE_SYSFS_GPIO=11`
  - `GATE_ACTIVE_HIGH=1`

## Flashing Instructions
1. Open Balena Etcher
2. Select `chrometech-edge-v1.0.7.img.xz`
3. Select target microSD card
4. Flash and boot the OrangePi

## First Boot Checklist
1. Confirm OrangePi boots cleanly
2. Confirm edge service starts
3. Confirm activation/trial flow works from Hub
4. Confirm coin slot stays off when idle and opens during insert mode
5. Confirm `₱5` and `₱10` reads are stable

## Integrity Verification
```bash
sha256sum -c chrometech-edge-v1.0.7.img.xz.sha256
```
