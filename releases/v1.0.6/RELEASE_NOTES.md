# ChromeTech PisoTAB Public Release v1.0.6

Date: 2026-04-06

## Summary
- OrangePi image rebuilt from the known-good `v1.0.2` bootable base by offline patching and PiShrink optimization.
- Edge backend was synchronized to the latest live OrangePi runtime behavior before image baking.
- Android Hub and Client `v1.0.6` APKs are included for the matching public release.

## Included Assets
- `android/chrometech-client-1.0.6-release.apk`
- `android/chrometech-hub-1.0.6-release.apk`
- `android/checksums.txt`
- `orangepi/chrometech-edge-v1.0.6.img.xz`
- `orangepi/chrometech-edge-v1.0.6.img.xz.sha256`

## OrangePi Runtime Parity
- Preserved the working production GPIO mapping from the live OrangePi backend:
  - coin input: `COIN_LINE=12`
  - relay gate: `GATE_LINE=11`
  - exported sysfs GPIO: `GATE_SYSFS_GPIO=11`
  - relay polarity: `GATE_ACTIVE_HIGH=1`
- Preserved current live coin timing tuning:
  - `COIN_GAP_MS=160`
  - `GATE_BETWEEN_COINS_MS=120`
  - `COIN_POST_COIN_COOLDOWN_MS=90`
- Embedded the current service pre-start GPIO export so the relay line is writable for `edgeapp` on boot.

## Image Hardening
- Replaced the embedded edge runtime with the updated source-of-truth backend files.
- Removed packaged databases and runtime leftovers:
  - `/opt/chrometech-edge/data/edge.db`
  - `/var/lib/vendo-edge/db.sqlite3`
  - `/opt/chrometech-edge/dev.sqlite3`
- Recreated `/opt/chrometech-edge/data` as `edgeapp:edgeapp` with mode `770` to avoid the readonly database issue on fresh flashed cards.
- Cleared `/etc/machine-id` and removed `/var/lib/dbus/machine-id` so flashed systems regenerate machine identity cleanly.
- Cleared Python cache files from the embedded runtime tree.

## Android Compatibility
- Recommended pair:
  - OrangePi image `v1.0.6`
  - Android Hub `1.0.6`
  - Android Client `1.0.6`
- This build is intended for the current Hub/Client release line and latest edge backend timing/power-gate behavior.

## Verification Performed
- Compared local edge backend against the live OrangePi runtime before baking the image.
- Verified the finished `v1.0.6` image contents after PiShrink:
  - correct GPIO env values present
  - service `ExecStartPre` present for gpio11 export
  - no packaged DB files remain
  - `/opt/chrometech-edge/data` exists and is writable for `edgeapp`
  - cloned machine-id state cleared
- Ran `xz -t` on the final image archive.
- Generated SHA-256 checksums for the Android APKs and the OrangePi image.

## Flashing
1. Flash `orangepi/chrometech-edge-v1.0.6.img.xz` using Balena Etcher.
2. Boot the OrangePi and allow first boot initialization to finish.
3. Install:
   - `android/chrometech-hub-1.0.6-release.apk` on the hub tablet
   - `android/chrometech-client-1.0.6-release.apk` on client tablets
4. Verify health:
   - `curl http://10.0.0.1:9000/health` in AP mode
   - or `curl http://<orangepi-lan-ip>:9000/health` on LAN
