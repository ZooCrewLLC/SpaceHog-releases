# Changelog

All notable changes to SpaceHog are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.0.6] - 2026-06-04

First public release.

### Fixed
- Switching drives mid-scan no longer leaves partial data labeled as a finished scan — returning to a drive whose scan was cancelled now correctly re-triggers a fresh scan
- Folder sizes no longer get corrupted by concurrent watcher-triggered sub-scans during a drive scan — fixes parents reporting smaller totals than their own children
- Folder rows now stay highlighted while any descendant is still being scanned, instead of going gray the moment the folder itself finishes

### Changed
- Releases now ship Windows and Linux builds only; macOS Universal builds are paused pending Apple Developer Program enrollment

## [1.0.5] - 2026-05-22

### Added
- Windows executable is now code-signed via Azure Trusted Signing — removes SmartScreen "unknown publisher" warnings on first run and shows ZooCrew, LLC as the verified publisher
- Linux release zip now includes README-linux.txt with libfuse2 setup instructions

### Fixed
- Drive panel free/used space now updates dynamically after each rescan and approximately every 10 seconds — previously required restarting the app to reflect deletions or changes made outside SpaceHog
- Linux: root-level files row now displays `/` instead of `\`

### Changed
- Default window size reduced to 1000×680; minimum window size reduced to 720×460

## [1.0.4] - 2026-05-14

### Added
- Linux: AppImage packaging — single portable executable, no installer required
- Linux: `.desktop` file for optional launcher integration

## [1.0.3] - 2026-05-13

### Added
- Drive panel hover tooltips showing used, free, and total space plus scanned file count
- Footer now shows combined total across all drives with percentage used

### Changed
- Trial enforcement: UI blocks scanning and shows a non-dismissible paywall once the 14-day trial expires
- Trial storage hardened: machine fingerprint, dual storage (Windows Registry + filesystem fallback), build-date floor prevents clock-rollback

## [1.0.2] - 2026-05-13

### Added
- Folders now default to a warm manilla color scheme
- README.txt included in all release packages

### Changed
- Free trial window changed from 30 days to 14 days
- Money-back guarantee period changed from 30 days to 14 days

## [1.0.1] - 2026-05-12

### Added
- macOS Photos Library is now scanned (file sizes only — no photos are accessed)
- `.app` bundle is built and signed in CI for consistent macOS TCC permission handling

### Fixed
- macOS CI build: `MetadataExt::st_flags()` and `fsid_t.val` transmute compatibility
- macOS: cloud storage placeholder files no longer inflate size counts
- macOS: cloud and virtual drives are excluded from the drive list
- macOS: repeated TCC permission prompts on every launch resolved
- Scanner: mtime-based cache skip rules now apply correctly on cache-hit paths

## [1.0.0] - 2026-05-11

Initial internal release.

### Features
- Fast recursive disk scanner for Windows, macOS (Universal), and Linux
- Interactive tree view with sortable and resizable columns
- Drive panel with usage bars and per-drive navigation
- Font picker: bundled Inter/Nunito or system font
- Settings: icon color customization for drives and folders
- Context menu: open any folder in Finder or Explorer
- Clear Cache option in the menu bar
- 14-day free trial; license activation via LemonSqueezy
- Windows, macOS Universal (arm64 + x86_64), and Linux builds
