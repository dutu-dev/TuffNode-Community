# TuffNode Community

Official binary distribution repository for **TuffNode Community**.

## Current release

**v0.6.0**

v0.6.0 is the current TuffNode Community release.

## Download

Windows installers are published through **GitHub Releases**:

https://github.com/dutu-dev/TuffNode-Community/releases

Installer name:

`TuffNode-Community-v0.6.0.exe`

## v0.6.0 highlights

### Desktop and UI

- Rebuilt dense Community administration shell.
- Runtime-selectable dark and light themes.
- Runtime accent-color selection.
- Notification Center with unread state, history and Silent Mode.
- Official application, installer and System Tray branding.
- Windows System Tray integration.
- Dynamic taskbar and tray status/telemetry.
- Start with Windows support.
- Configurable Minimize-to-Tray / Exit behavior.
- 18 bundled offline languages.

### Server creation

- Reworked Create Server modal with fixed header/footer and scrollable body.
- Smart Minecraft port selection.
- Automatic compatible Java / Eclipse Temurin provisioning.
- Separate minimum and maximum RAM allocation.
- RAM limits use total installed physical memory rather than current free memory.
- Optional Geyser / Bedrock support.
- Managed 64 × 64 server icons.
- Duplicate-create race protection.

### Server management

- Dense searchable/filterable Servers table.
- Stable catalogue reconciliation without clearing/rebuilding the full UI list.
- Fixed first-load duplicate server rows.
- Fixed server-list flicker and disappearing rows.
- External `server.properties` changes synchronize back into TuffNode, including port changes.
- Improved managed/imported server deletion behavior.
- Locked-file deletion retries for Java/JAR files still in use.

### Workspace

- Modular Overview, Console, Players, Add-ons, Backups, Config and Files views.
- Provider-aware configuration discovery and raw editing.
- Live server PID, CPU and memory telemetry.
- Live player telemetry.
- Rebuilt Add-ons Catalog / Installed workflows.
- Optional anticheat detection and Grim recommendation flow.
- Improved backup and scheduler behavior.

### Reliability

- Application-wide exception boundary for recoverable UI/async failures.
- Guarded background operations across runtime, tray, Shield, add-ons and loaded views.
- User-facing error dialogs for recoverable failures.
- Hardened WPF bindings and nullable image-source handling.
- Windows/.NET 10 CI validation.
- **0 warnings**
- **0 errors**
- **69 / 69 tests passing**

## What is published here

This repository is intentionally distribution-only.

- Windows installer executables
- Release notes
- Changelog
- Public release information

**The TuffNode application source code is not published in this repository.**

## About TuffNode Community

TuffNode Community is a free Windows application for creating, importing and managing self-hosted Minecraft servers.

It includes server lifecycle management, Java runtime handling, console and player tools, add-on browsing and installation, installed add-on management, backups, networking tools, Shield controls, configurable JVM memory/arguments and optional Java/Bedrock cross-play through Geyser.

## Platform

- Windows 10/11 x64
- Self-hosted Minecraft Java servers

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## v0.6.0 release notes

See [RELEASE-NOTES-v0.6.0.md](RELEASE-NOTES-v0.6.0.md).

## Source availability

TuffNode Community is not open source. The application source code is maintained separately and is not distributed through this repository.

## Contact

contact@tuffnode.com

https://tuffnode.com
