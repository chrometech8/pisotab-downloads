# ChromeTech PisoTAB Public Release v1.0.7

Date: 2026-04-06

## Summary
- This is the current stable Android release.
- Includes the client lock-screen return fix and related client-screen stability improvements.
- OrangePi compatibility remains pinned to the same proven image from `v1.0.6`.

## Android Assets
- `android/chrometech-client-1.0.7-release.apk`
- `android/chrometech-hub-1.0.7-release.apk`
- `android/checksums.txt`

## Stable Version Note
- Recommended stable Android version: `1.0.7`
- This release is intended as the stable Hub/Client APK pair for the current OrangePi backend/image line.

## Fixed Issue
- Fixed client behavior where the session was not reliably returning to the client lock screen at the correct timeout boundary.

## OrangePi Compatibility
- Keep using the same OrangePi image from `v1.0.6`:
  - `releases/v1.0.6/orangepi/chrometech-edge-v1.0.6.img.xz`
- No new OrangePi image is required for this Android-only release.

## Validation
- APK SHA-256 hashes are provided in `android/checksums.txt`.
- Install matching Hub and Client `1.0.7` builds together.
