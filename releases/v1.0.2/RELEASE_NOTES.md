# ChromeTech PisoTAB Public Release v1.0.2

Date: 2026-04-04

## Summary
- OrangePi image rebuilt from `v1.0.1` base by offline patching the bootable image filesystem (no live raw SD capture).
- Edge backend was compared against the live OrangePi server first, then synchronized to source-of-truth with the latest server behavior.
- Payment capture open-screen stability hardening was included to reduce rapid-tap race failures.

## Included Assets
- `android/chrometech-client-1.0.2-release.apk`
- `android/chrometech-hub-1.0.2-release.apk`
- `orangepi/chrometech-edge-v1.0.2.img.xz`
- `orangepi/chrometech-edge-v1.0.2.img.xz.sha256`

## Backend Parity and Fixes
- Synced `payment_capture.py` logic from the latest running OrangePi backend into source-of-truth.
- Kept source-of-truth `db.py` pairing safety logic (deterministic pairing; no implicit stale fallback pairing).
- Kept source-of-truth `main.py` router wiring including `vip_flow`.
- Added idempotent hub payment start behavior for same-target rearm to reduce `open screen failed` during rapid taps.
- Added payment lifecycle logging in `/api/v1/hub/payment` routes and capture state transitions.

## Image Hardening
- Patched image backend files directly under `/opt/chrometech-edge/app/`.
- Enforced backend file ownership to `edgeapp:edgeapp` with restrictive runtime-safe permissions.
- Enforced `/opt/chrometech-edge/data` directory ownership and mode for writable runtime DB creation.
- Removed packaged `/opt/chrometech-edge/data/edge.db` so first boot initializes a fresh clean database.

## Verification Performed
- New image archive integrity check: `xz -t`
- Checksum generated for release artifact.
- Root filesystem inspection verified updated backend files and edge data-path permissions.
- Partition table preserved (bootable DOS label + Linux partition).

## Android Compatibility Patch Notes (for OrangePi v1.0.2)
- Recommended pair: OrangePi image `v1.0.2` with Android Hub/Client APKs `v1.0.2`.
- Compatibility target: Android 11+ tablets for Hub and Client.
- Hub tile/open-coin flow is hardened for rapid tap behavior to reduce `open screen failed` race scenarios.
- Client watchdog/idle behavior is tuned to reduce unintended wake/reopen loops while idle.
- Use matching Hub and Client release versions (`1.0.2` / `1.0.2`) to avoid protocol/state mismatch.

## Flashing
1. Flash `orangepi/chrometech-edge-v1.0.2.img.xz` using Balena Etcher.
2. Boot OrangePi and wait for edge service startup.
3. Install:
   - `android/chrometech-hub-1.0.2-release.apk` on the hub tablet
   - `android/chrometech-client-1.0.2-release.apk` on client tablets
4. Verify health:
   - `curl http://10.0.0.1:9000/health` (AP mode)
   - or `curl http://<orangepi-lan-ip>:9000/health`
