# Android v1.0.9

## Stable Release
This is the current stable Android release.

## Fixes
- Fixed Hub activation flow so license activation no longer falls into `Listen error HTTP 401`.
- Fixed Hub System page session-expired login loop caused by activation state auth mismatch.
- Added Hub boot initialization flow so local admin login starts in a cleaner, more reliable state.
- Added Hub System `APP CONTROL` actions:
  - `Launcher`
  - `Exit App`

## Compatibility
- Compatible OrangePi image remains:
  - `releases/v1.0.6/orangepi/chrometech-edge-v1.0.6.img.xz`

## Android Assets
- `chrometech-client-1.0.9-release.apk`
- `chrometech-hub-1.0.9-release.apk`
