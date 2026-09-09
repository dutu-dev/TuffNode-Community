# TuffNode Community v0.6.0-rc.1

**Release Candidate 1**

TuffNode Community v0.6.0-rc.1 is the first release candidate for the v0.6.0 Community line.

This build focuses on final UI polish, server-management stability, desktop integration and application-wide reliability before the stable v0.6.0 release.

> This is a pre-release build. It is intended for final validation and may still receive release-blocking fixes before v0.6.0 stable.

## Highlights

### New desktop experience

- Rebuilt dense Community administration shell.
- Dark and light runtime themes.
- Runtime accent-color selection.
- Notification Center with persistent history, unread state and Silent Mode.
- Official TuffNode application, installer and System Tray branding.
- Windows System Tray integration with idle/running/alert states.
- Dynamic taskbar and tray server telemetry.
- Start TuffNode with Windows support.
- Configurable close behavior: Minimize to Tray or Exit.
- 18 bundled offline languages.

### Smarter server creation

- Fixed three-row Create Server modal with scrollable content.
- Smart port selection: prefers 25565 and selects a free fallback when needed.
- Automatic compatible Java / Eclipse Temurin provisioning.
- Separate minimum and maximum RAM allocation.
- RAM allocation uses total physical memory as its upper bound.
- Configurations above currently free RAM remain allowed with an informational warning.
- Optional Geyser / Bedrock setup.
- Managed 64 × 64 Minecraft server icons.
- Duplicate-create race protection.

### Servers catalogue stability

- Reworked server catalogue reconciliation.
- Fixed servers disappearing after Start.
- Fixed first-navigation ghost/flicker rows.
- Fixed the WPF first-load race that could temporarily show the same server twice.
- Added defensive catalogue deduplication.
- External `server.properties` changes now synchronize operational metadata such as server port back into TuffNode.
- Improved imported/reconnected server synchronization.

### Administration workspace

- Modular Overview, Console, Players, Add-ons, Backups, Config and Files pages.
- Provider-aware raw configuration discovery/editing.
- Live PID, CPU and memory telemetry.
- Live player telemetry.
- Rebuilt Add-ons Catalog and Installed workflows.
- Local plugin/mod management.
- Optional anticheat detection and Grim recommendation flow.
- Improved backup/scheduler behavior.

### Reliability and error handling

- Added an application-wide exception boundary for recoverable UI and async failures.
- Guarded background tasks across runtime, Shield, tray, add-ons and loaded views.
- Added user-facing error dialogs for recoverable failures.
- Hardened managed-server deletion when files remain temporarily locked.
- Added locked-file deletion retries.
- Fixed WPF binding diagnostics and nullable image-source conversion failures.
- Fatal process-level faults remain fatal rather than being silently swallowed.

## Validation

- Windows / .NET 10
- Build with warnings treated as errors
- **0 warnings**
- **0 errors**
- **69 / 69 tests passing**

## Installer

Attach the Windows installer to the GitHub Release using:

`TuffNode-Community-v0.6.0-rc.1.exe`

Recommended GitHub Release settings:

- **Tag:** `v0.6.0-rc.1`
- **Release title:** `TuffNode Community v0.6.0-rc.1`
- **Target:** the release/distribution repository `main` branch
- **Mark as pre-release:** Yes
- **Mark as latest:** No

## Upgrade note

This release candidate is part of the Community line. Community and TuffNode Lite use independent version histories and release cadences.

## Feedback

For bug reports and release-candidate feedback:

contact@tuffnode.com

https://tuffnode.com
