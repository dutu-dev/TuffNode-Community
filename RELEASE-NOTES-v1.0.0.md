# TuffNode Community v1.0.0

## Release status

TuffNode Community v1.0.0 is the first stable Community release after the 0.7.x development cycle.

## Highlights

### Reliability and security

- Hardened managed and imported server path confinement.
- Added safe handling for filesystem roots, reparse points, unsafe Windows filenames and command-interpreter metacharacters.
- Added bounded HTTPS-only downloads with redirect validation, size limits and hash metadata validation.
- Hardened managed Java and add-on downloads and archive extraction.
- Added archive traversal, symlink, entry-count and expanded-size protection.
- Serialized server mutations, add-on operations, backups, restore, move and delete operations.
- Improved Shield ownership tracking and reconciliation so TuffNode does not remove operator- or plugin-owned bans.
- Added bounded application log rotation and secret redaction for credentials, tokens, connection strings and private-key blocks.
- Installer launch uses the original user token instead of Setup elevation.

### Server management

- Improved server metadata normalization and catalog recovery.
- Added safer create, import, update, move and delete flows.
- Added runtime maintenance coordination during JAR replacement and server updates.
- Start and Restart are disabled while an update transaction is active.
- Preserved pre-update backups for explicit recovery.

### Add-ons and backups

- Added provider checksum and declared-size verification where available.
- Added cancellation-safe archive validation and background processing.
- Improved atomic replacement and rollback behavior.
- Added bounded backup restore limits and reparse-point checks.
- Preserved user files outside the managed add-on target.

### Desktop and update experience

- Removed unused legacy UI artifacts.
- Added GitHub Releases update checks against the public `dutu-dev/TuffNode-Community` repository.
- Automatic update checks run at most once every seven days.
- Added manual **Check for updates** and **View release notes** actions.
- Updates are not downloaded or installed automatically.
- Preserved Community themes, localization, runtime controls, networking diagnostics, Shield and tray behavior.

## Installer

Installer entry points:

`installer/build-installer.ps1`

`installer/TuffNodeSetup.iss`

Expected installer:

`TuffNode-Community-v1.0.0.exe`

The release bundle includes:

- `TuffNode-Community-v1.0.0.exe`
- `TuffNode-Community-v1.0.0.exe.sha256`
- `checksums.txt`
- `TuffNode-Community-v1.0.0.release.json`

The installer preserves the existing Community AppId for in-place upgrades from 0.7.6.

## Scope

Community remains the local Windows desktop edition for self-hosted Minecraft server administration. Remote-management and Core-only features are outside this release.

## Requirements

- Windows 10/11 x64
- Administrator approval for installation into Program Files
- Internet access for server software, Java runtimes, add-ons and release metadata

## Distribution

Official binaries are published manually in:

https://github.com/dutu-dev/TuffNode-Community/releases

Support:

contact@tuffnode.com
