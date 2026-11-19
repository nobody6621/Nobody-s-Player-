# Nobody's Player — Android release readiness

This checklist is the final manual gate for the Android-first release. A green CI run is necessary but does not replace testing on a physical Android device.

## Build variants
- [ ] Run shared core unit tests: `./gradlew :core:testDebugUnitTest`
- [ ] Run lyrics unit tests: `./gradlew :lyrics:testDebugUnitTest`
- [ ] Run Universal FOSS unit tests: `./gradlew :app:testUniversalFossDebugUnitTest`
- [ ] Run Universal GMS unit tests: `./gradlew :app:testUniversalGmsDebugUnitTest`
- [ ] Build Universal FOSS debug APK: `./gradlew :app:assembleUniversalFossDebug`
- [ ] Build Universal GMS debug APK: `./gradlew :app:assembleUniversalGmsDebug`
- [ ] Build signed Universal GMS release APK only when release signing secrets are configured.

## Device acceptance
- [ ] Install and launch on Android 8+ (minimum supported API 26).
- [ ] Confirm Android 12+ splash screen uses the deep-violet launch surface.
- [ ] Sign in / browse catalog and confirm artwork, search, album and playlist screens load.
- [ ] Start, pause, seek, skip, repeat and shuffle playback.
- [ ] Verify queue editing, lyrics synchronization and background playback.
- [ ] Verify download / offline playback and storage permission flows.
- [ ] Verify audio focus, Bluetooth headset controls and notification actions.
- [ ] Verify cast on GMS build; confirm FOSS build does not expose unavailable Cast behavior.
- [ ] Rotate screen, background/restore app, and test process recreation.
- [ ] Check light theme, dark theme, monochrome theme and large font/display scaling.
- [ ] Confirm app update/install behavior preserves existing app data and package identity.

## Release identity and compatibility
- Application ID remains `echo.music.iad1tya`.
- Namespace remains `echo.music.iad1tya`.
- Keep upstream GPL-3.0 notices and provide corresponding source for distributed derivatives.
- Review all third-party dependencies, fonts, artwork and branding licenses before publishing.
- Never publish a release APK until signing configuration, versioning, privacy policy and store metadata are reviewed.
