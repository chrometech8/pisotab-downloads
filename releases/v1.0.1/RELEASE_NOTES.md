# ChromeTech PisoTAB Public Release v1.0.1

## Status
- This is the production-ready public maintenance release for ChromeTech PisoTAB.
- This release fixes a contaminated Orange Pi image database baseline found in the earlier public image.

## Included Assets
### Android
- `android/chrometech-client-v1.0.0-release.apk`
- `android/chrometech-hub-v1.0.0-release.apk`
- `android/checksums.txt`

### Orange Pi
- `orangepi/chrometech-edge-v1.0.1.img.xz`
- `orangepi/chrometech-edge-v1.0.1.img.xz.sha256`

## What Changed
- Rebuilt the Orange Pi image from the current stable image base with a verified clean edge database.
- Removed stale activation state, paired tablets, sessions, users, and sales data from the shipped edge database.
- Verified the packaged image boots with an empty `activation_state` (`PENDING`) and zero tablet/session/user rows.

## Production Readiness Notes
- Edge auto-pair remains disabled by default in the shipped image.
- The image now starts from a clean machine baseline suitable for new deployments.
- Android APK assets are unchanged from the previous public release set.

## Install Notes
- Flash `orangepi/chrometech-edge-v1.0.1.img.xz` with Balena Etcher.
- Install the bundled Android Hub and Client APKs after flashing.
- For the safest pairing experience, let the client tablet finish first boot and register before pairing from the hub.

- Hotfix: corrected `/opt/chrometech-edge/data/edge.db` ownership/permissions to `edgeapp:edgeapp` with writable mode for runtime init on freshly flashed SD cards.
