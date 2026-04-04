# ChromeTech PisoTAB v1.0.4

## Summary
This release publishes updated Android Hub and Client APKs with a targeted fix for the client permission flow.

## Android Assets
- `android/chrometech-hub-1.0.4-release.apk`
- `android/chrometech-client-1.0.4-release.apk`
- `android/checksums.txt`

## Fixed Issues
- Fixed a client issue where **Enable Display Over Apps** could get stuck on screen after admin setup.
- Improved overlay permission state refresh on app resume/start.
- Added a safe dismiss path so the overlay permission prompt no longer blocks the client flow.

## OrangePi Compatibility
- Keep using the same OrangePi image from **v1.0.2** for compatibility:
  - `releases/v1.0.2/orangepi/chrometech-edge-v1.0.2.img.xz`

## Validation
- APK SHA-256 hashes are provided in `android/checksums.txt`.
