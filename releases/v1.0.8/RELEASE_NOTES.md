# ChromeTech PisoTAB Public Release v1.0.8

Date: 2026-04-06

## Summary
- Updated Android Hub and Client APKs with the hub boot/auth flow fix.
- Prevents the activation/settings flow from racing ahead before local admin login is ready.

## Android Assets
- `android/chrometech-client-1.0.8-release.apk`
- `android/chrometech-hub-1.0.8-release.apk`
- `android/checksums.txt`

## Compatibility Sidenote
- Compatible OrangePi image: `v1.0.6`
- Keep using the same OrangePi image:
  - `releases/v1.0.6/orangepi/chrometech-edge-v1.0.6.img.xz`
- No new OrangePi image is required for this Android-only update.

## Fixed Issue
- Fixed hub boot behavior so admin-only activation/settings flows wait for local admin authentication instead of entering a missing-token state too early.

## Validation
- APK SHA-256 hashes are provided in `android/checksums.txt`.
- Install matching Hub and Client `1.0.8` builds together.
