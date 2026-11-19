# Nobody's Player — Product Direction

## Product goal

Turn this repository into **Nobody's Player**, a polished music-listening product with a futuristic neon visual identity and clients for Android, iOS, and the web.

The existing Echo Music application is a substantial native Android/Kotlin + Jetpack Compose codebase. Its current Android playback, library, lyrics, and discovery features should be preserved where technically and legally possible. The existing `applecanvas` module is an Android feature module, not a native iOS application.

## Product principles

- **One product identity:** Nobody's Player, with a consistent design language across supported clients.
- **Futuristic, usable UI:** dark surfaces, restrained neon accents, depth and motion used to clarify hierarchy rather than distract.
- **Reliable playback first:** queue, play/pause, seek, background playback, media controls, and recovery from network interruptions.
- **User-owned library:** playlists, favourites, listening history, and preferences should be portable between clients where provider terms permit.
- **Accessible by default:** readable contrast, scalable text, keyboard support on web, and reduced-motion support.
- **Provider-aware catalogue:** search and playback must use documented or otherwise authorized provider capabilities. Catalogue size, playback availability, offline use, and regional access depend on provider terms and rights.

## Platform strategy

### Android

Keep the existing Kotlin/Compose app as the first-class Android client. Rebrand in a controlled sequence, then modernize its design system and playback screens without removing existing functionality. Keep application identifiers and signing configuration stable until a deliberate migration plan is approved.

### iOS

Build a separate native iOS client (SwiftUI) or a clearly defined cross-platform client after the shared product contracts are stable. Do not treat the existing Android `applecanvas` module as an iOS application. Reuse backend contracts and design tokens, not Android-only implementation details.

### Web

Build a responsive web client/PWA with accessible navigation, search, library, playlists, and a persistent player. Browser playback must respect browser autoplay rules and provider embedding/playback restrictions. Offline support is limited to content and caching that providers explicitly permit.

## Shared service boundaries

Keep provider integrations behind replaceable interfaces:

- Catalogue/search provider
- Playback/session provider
- Lyrics provider
- User identity and sync service
- Library and playlist service

Avoid coupling the new clients directly to undocumented provider endpoints. Do not implement DRM circumvention, paywall bypass, credential harvesting, or unauthorized copying/hosting of music.

## Suggested delivery sequence

1. **Baseline and safety:** document the upstream baseline, license obligations, build requirements, and existing features; create a clean feature branch.
2. **Android identity and design system:** app naming, icons, typography, color tokens, navigation, player and mini-player refresh.
3. **Web MVP:** responsive browse/search/library/player shell with a provider adapter and clear unavailable/unsupported states.
4. **Shared account and sync:** define authentication, playlists, favourites, and history contracts; add a backend only where cross-device sync is needed.
5. **iOS MVP:** implement the same product contracts and design language using supported iOS playback capabilities.
6. **Quality and release:** automated tests, accessibility checks, privacy review, provider-policy review, signing, and store-specific release preparation.

## License and attribution

This repository contains GPL-3.0-licensed upstream code. Preserve the license and required notices, identify modifications, and satisfy GPL-3.0 source-distribution requirements when distributing derivative binaries. Review each bundled dependency and asset for its own license before release. This document does not replace legal review.

## Current implementation status

This file records the product direction only. It does not claim that iOS, web playback, account synchronization, or a new catalogue provider has been implemented. Platform work should be merged only after the relevant client can be built and its supported playback path tested.
