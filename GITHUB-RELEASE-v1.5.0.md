# GitHub Release — TuffNode Community v1.5.0

**Tag:** `v1.5.0`  
**Release title:** `TuffNode Community v1.5.0`  
**Release type:** Stable (not a prerelease)  
**Baseline:** Last public release `v1.0.1` (October 27, 2026)

> **Maintainer note (remove from the GitHub release body):** This file is the prepared GitHub release text. Upload the installer and its actual generated checksum/manifest assets before publishing. Do not invent checksum values or mark a release published before the downloadable installer exists.

## What's new since v1.0.1

TuffNode Community v1.5.0 is the next public Windows desktop release after v1.0.1. All development through internal versions 1.0.2–1.4.x is included in this cumulative update; those were not separate public stable releases.

### Server administration & performance

- Refined Home, Servers and server management workspaces, status indicators, filtering and creation-date sorting.
- Improved server creation/import, Java process lifecycle, settings and save operations.
- Added TPS monitoring for compatible Minecraft server software, sampled approximately every 10 seconds and shared between views.
- Improved CPU/RAM/TPS presentation and Network address management.

### Player details & Chat

- Added richer player information, live inventory inspection and saved-playerdata fallback.
- Added supported Ender Chest, Bundle and nested Shulker Box inspection.
- Added a dedicated **Chat** tab with player messages, conversation bubbles, a composer, server announcements and per-session message/draft retention.
- Improved console autocomplete, command arguments, player suggestions and keyboard interactions.

### Security, backup and reliability

- Introduced signed security-patch staging with explicit approval, rollback and recovery.
- Improved Shield protections, server-side integration, block/trust management and operational notifications.
- Hardened backup and ZIP integrity checks, paths, downloads, URLs, redirects, DNS target validation and content limits.
- Kept standard portable ZIP backups; experimental encryption variants were intentionally removed.

### Appearance, localization & privacy

- Added Catppuccin Mocha, Tokyo Night, Nord Arctic, Dracula and Rosé Pine Dawn themes.
- Refined window chrome, modal dialogs, toolbars, alignments, loading feedback and notification interactions.
- Updated all **18 bundled language resources**.
- Improved local data-retention controls and aligned privacy information with [Privacy & Responsible Use](https://tuffnode.com/privacy).
- Removed remote MCHeads player-image loading and experimental network traffic tracking.

## Full, authoritative changelog

The complete v1.0.1 → v1.5.0 changelog is maintained in the public distribution repository and displayed on the website:

- [Complete v1.5.0 changelog](https://github.com/dutu-dev/TuffNode-Community/blob/main/CHANGELOG.md)
- [TuffNode website changelog](https://tuffnode.com/changelog)

These are the canonical release-change descriptions; this GitHub Release body is a readable summary.

## Installation & compatibility

- Intended platform: supported Windows x64 versions for the .NET 10 desktop application.
- Existing TuffNode Community installations are intended to upgrade in place.
- Back up important Minecraft worlds, server configuration and add-ons before installing.
- TPS requires a compatible Minecraft server command. Chat recognizes standard player-chat console formats; third-party plugin formats may differ.
- Community does **not** include Core/Direct Connect functionality.

## Downloads and verification

Attach the following files produced by the final local Windows build:

- `TuffNode-Community-v1.5.0.exe` — Windows installer
- `TuffNode-Community-v1.5.0.exe.sha256` — SHA-256 checksum
- `checksums.txt` — checksum list
- `TuffNode-Community-v1.5.0.release.json` — release metadata

Verify the installer SHA-256 against the attached checksum file. The checksum must match the **final installer bytes**, including any Authenticode signature.

## Before pressing Publish release (maintainer checklist, remove from final body)

- [ ] Merge the release-preparation PR into `dutu-dev/TuffNode-Community/main`.
- [ ] Generate the installer locally from the correct frozen Community source commit.
- [ ] Confirm installer filename/version and that an upgrade from v1.0.1 works.
- [ ] Upload the installer plus the generated checksum and manifest files.
- [ ] Verify the actual SHA-256 after upload.
- [ ] Set tag `v1.5.0` and title `TuffNode Community v1.5.0`.
- [ ] Select stable release, not prerelease.
- [ ] Publish; after publication, synchronize the website download metadata while preserving the changelog entry.
