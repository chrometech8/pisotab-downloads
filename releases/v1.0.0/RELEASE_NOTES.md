# ChromeTech PisoTAB Public Release v1.0.0

## Status
- This is the first public stable release set for ChromeTech PisoTAB.

## Included Assets
### Android
- `android/chrometech-client-v1.0.0-release.apk`
- `android/chrometech-hub-v1.0.0-release.apk`
- `android/checksums.txt`

### Orange Pi
- `orangepi/chrometech-edge-v1.0.0.img.xz`
- `orangepi/chrometech-edge-v1.0.0.img.xz.sha256`

## Source Versions Used
- Android package source: stable Android `android-v1.0.11`
- Orange Pi image source: stable edge image `edge-image-v1.0.4`

## Stable Notes
- Android APKs are signed release builds
- Android release workflow now verifies APKs are non-testOnly before publishing
- Orange Pi image includes the advanced-settings privilege fix for shutdown, reboot, SSH enable/disable, and dnsmasq-backed admin actions
- Orange Pi image was captured with a clean DB baseline

## Install Notes
- If a device still has an app signed by an older lost keystore, uninstall/reinstall may be required
- Use Balena Etcher to flash the Orange Pi image
- Pair this Android and Orange Pi set together for the intended stable deployment
