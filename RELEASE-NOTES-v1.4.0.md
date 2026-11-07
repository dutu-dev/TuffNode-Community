# TuffNode Community v1.4.0

**Security, reliability and administration update**  
Release date: 2026-11-07  
Platform: Windows 10/11 x64

TuffNode Community v1.4.0 consolidates the work delivered since the last public release, v1.0.1. Intermediate development and testing builds were not published as stable releases.

## Security updates

### Signed security-patch channel

- Added a security-update channel backed by the public `dutu-dev/TuffNode-Community.SecurityUpdates` repository.
- The updater checks GitHub Releases for the latest signed patch.
- The manifest is verified using the publisher public key pinned in the application (RSA-3072).
- Package SHA-256, asset size, patch sequence, application compatibility and manifest validity are checked before a patch can be installed.
- Downloaded patches are staged locally and shown in the Security area.
- **Installation always requires explicit user approval.** Downloads and verification can happen automatically; applying a patch never happens without consent.

### Transactional installation and recovery

- Added a dedicated PatchRunner process so application files can be updated after TuffNode closes.
- Added a TuffNode-branded WPF maintenance window with progress for signature verification, compatibility checks, package validation, file application, rollback/recovery and restart.
- Added a durable transaction journal and verified file backups.
- Added rollback when an operation fails and recovery after process termination or an interrupted update.
- Recovery validates the signed manifest, patch package, journal and backup hashes before restoring files.
- The helper requests elevation only when the installation directory requires it and attempts to relaunch TuffNode without inheriting an elevated token.
- The existing Community installation identity is preserved for in-place upgrades.

### Download and archive hardening

- Added trusted-host and public-address validation for security-update downloads, including redirect handling.
- Hardened patch archive validation against path traversal, reparse points, duplicate or case-colliding entries, unexpected files, oversized payloads and unsafe destinations.
- Added strict manifest and operation-path validation.

## Server administration

- Added live Minecraft player inventory inspection.
- Added inspection of Ender Chests, Bundles and Shulker Boxes, including nested containers.
- Expanded player details with additional gameplay information.
- Added console command autocomplete for commands, arguments, online players and selectors.
- Added an Activity Timeline for server events, warnings, errors and backup operations.
- Added Diagnostic Bundle generation for troubleshooting, with sensitive data redacted before export.
- Improved add-on catalog loading through lazy loading.

## Reliability and interface

- Added SHA-256 integrity verification for backups.
- Hardened ZIP archive validation, including entry metadata, file sizes and CRC/integrity checks.
- Improved archive path-traversal protections.
- Continued interface consistency and usability refinements across Community workspaces, including alignment, spacing, loading states and interaction feedback.
- Improved diagnostics and localization.

## Installation and compatibility

- Windows 10/11 x64.
- .NET 10 desktop application.
- Existing TuffNode Community installations upgrade in place.
- Security patches are downloaded and verified separately from the main application installer. Applying a security patch requires explicit user approval.
- The Windows installer is distributed as a standalone executable through the official GitHub Releases page.

## Release bundle

- `TuffNode-Community-v1.4.0.exe` — Windows installer.
- `TuffNode-Community-v1.4.0.exe.sha256` — installer SHA-256 sidecar.
- `checksums.txt` — release checksum list.
- `TuffNode-Community-v1.4.0.release.json` — structured release manifest.

## Notes

- TuffNode Community remains proprietary software; this release does not change its licensing model.
- Minecraft and third-party server implementations, plugins, mods and services remain subject to their own licenses and terms.
- Security scanning and automated tests are validation measures, not a guarantee that software is free of vulnerabilities.
