# TuffNode Community v1.5.0 — Release Notes

The versioned installer and checksum assets are distributed through the official GitHub Release, not through this repository's source history.  
**Comparison:** last public stable release **v1.0.1 (27 October 2026)** → **v1.5.0**  
**Platform:** Windows x64, subject to the support requirements in [README.md](README.md).

> Versions 1.0.2–1.4.x were internal development/testing milestones, not intervening public stable releases. These notes are cumulative: users upgrading from v1.0.1 receive the changes described below. They document the changes present in the release source; verify the final installer before distribution.

## Highlights

- Richer local Minecraft server management, including live player details and inventory/container inspection.
- Server dashboards, resource metrics, per-server status and more consistent server configuration workflows.
- A dedicated **Chat** tab presenting player chat separately from diagnostic console output, with the ability to send server messages.
- **TPS monitoring** for supported server implementations, sampled via a captured console command at 10-second intervals while monitored. Unsupported or unavailable values appear as an em dash.
- More capable console command entry, add-on management and operational diagnostics.
- Stronger safeguards around backups, file paths, downloads, archive processing and the security-update channel.
- A refreshed Network page, additional appearance themes, typography/layout refinements and offline localization.
- Updated privacy and responsible-use presentation with a canonical public notice.

## Server management and operations

- Improved the Home, Servers and server-detail workspaces, with recent-server and active-server information, status and process/resource telemetry.
- Added live per-process CPU, RAM, PID and uptime displays where available; removed redundant PID presentation and reorganized dashboard metrics.
- Added TPS in Home, Network, Servers and the server overview. The application shares each server's sample across views instead of issuing duplicate polls. The supported `tps` console response is parsed; a stopped or unsupported server displays `—`.
- Improved server settings controls and visual save operations, including whitelist, PvP and online-mode configuration workflows.
- Refined server creation, import, navigation and sorting, with common control sizes and spacing.
- Improved server-lifecycle behavior and information for processes that are starting, running, stopping or stopped.

## Players, inventories and Chat

- Added live player inventory inspection and expanded player details.
- Added inspection of inventory/equipment, Ender Chest and supported nested inventory items (Bundles/Shulker Boxes), where the Minecraft server and available data permit.
- Improved player-history metadata and interactive refresh controls.
- Added a **Chat** workspace that extracts standard player chat events from the managed server's console stream; ordinary system logs and arbitrary console output are not shown as chat.
- Chat displays messages in conversation bubbles, with player names, time, visually distinct outgoing server messages, auto-scroll and a fixed message composer.
- Messages sent from TuffNode use the Minecraft `say` command. Recent chat and unsent drafts remain in memory per server during navigation; they are **not** a durable chat archive and are not guaranteed to survive an application restart.
- Custom third-party chat plugin formats may not be recognized by the standard parser.

## Console, add-ons and administration

- Expanded console command autocomplete and argument/player suggestions.
- Improved add-on discovery, catalog loading, installed add-on management and responsive control states.
- Continued adjustments to file management, backups, loading feedback and desktop administration dialogs.
- Improved network information, including local/public address copying, status and tooltips where the explanations provide technical context.

## Security and data integrity

- Strengthened validation of downloaded content, allowed destinations, URLs, redirects and external network addresses to reduce unsafe-download, SSRF and DNS-rebinding exposure.
- Added or improved archive checks, including path confinement, unsafe entry rejection, metadata and integrity validation.
- Strengthened backup archive verification, including SHA-256 integrity mechanisms and ZIP validation, with safeguards against archive path traversal.
- Added a signed security-patch workflow with staging, compatibility/integrity checks, explicit user consent before installation, transactional application and rollback/recovery logic.
- Improved protection against invalid player identifiers entering privileged Minecraft commands.
- Updated security-related dependencies and automated security gates.
- No software release can be certified as having zero vulnerabilities. Security checks remain part of the release gate.

## Appearance, localization and desktop UI

- Added Catppuccin Mocha, Tokyo Night, Nord Arctic, Dracula and Rosé Pine Dawn palettes. **Gruvbox was removed** and is not shipped as an appearance option.
- Corrected theme palette resources and adjusted overlay colors and rendering behavior.
- Improved navigation, window resizing/maximization, notification badge placement, modal spacing and common action-button sizes.
- Aligned server resource labels and values (CPU/RAM/TPS), Network status counters, Player Details refresh/timestamp controls, and various tables and cards.
- Standardized dashboard typography using Segoe UI and retained monospace in appropriate diagnostic/editor contexts.
- Added contextual information icons where relevant, rather than indiscriminately adding them to every field.
- Updated the bundled localization keys for new features across all 18 supported languages.

## Privacy, responsible use and external services

- The canonical notice is [Privacy & Responsible Use](https://tuffnode.com/privacy); the installer requests a separate acknowledgement alongside the software license.
- The application manages local server-related information. Its use of Minecraft and third-party services is described by the notice; users remain responsible for the Minecraft server and configuration they operate.
- Removed the external MCHeads player-image feature and related automatic external player-image requests.
- See [Privacy & Responsible Use Notice](https://tuffnode.com/privacy) and [security reporting](https://github.com/dutu-dev/TuffNode-Community/security).

## Installation / upgrade

The intended release bundle, **to be generated and verified after the release build**, contains:

| Asset | Purpose |
| --- | --- |
| `TuffNode-Community-v1.5.0.exe` | Windows installer |
| `TuffNode-Community-v1.5.0.exe.sha256` | Installer checksum |
| `checksums.txt` | Release checksum list |
| `TuffNode-Community-v1.5.0.release.json` | Machine-readable release metadata |

- Preserve the existing Community application identity so an older Community installation can upgrade in place.
- Take independent backups of valuable worlds and configuration before upgrading.
- Minecraft itself, server distributions, Java runtimes, add-ons and third-party services retain their own licenses and policies.
- This version does **not** include Direct Connect/Core remote functionality.

## Known limitations and release verification

This documentation is not a substitute for Windows release-mode build, installation/upgrade/uninstall smoke tests, Windows 100%/125%/150% DPI checks, theme-switch rendering, real TPS sampling on supported and unsupported Minecraft servers, Chat parsing with different server/plugin log formats, patch recovery and backup restore end-to-end tests.

Current known limitations:
- TPS requires a compatible server-side `tps` command; a blank/dash reading is not an indication of healthy tick rate.
- Chat is based on recognized console message patterns and keeps only bounded in-memory session history.
- Some visual fixes depend on Windows desktop compositing, display scale and theme and must be checked on the target system.

For the maintainer's release process, follow the maintainer's private release checklist.

## Additional changes included in this cumulative release

Beyond the highlighted items above, v1.5.0 includes numerous targeted fixes across notification handling and themed dialogs, low disk-space warnings, server failure and scheduled-backup alerts, optional three-layer Shield protections, trusted/blocked IP lists, Windows Firewall integration, security-patch consent and recovery, server-content path validation, add-on icon caching and installed metadata, backup integrity and sensitive server.properties sanitization, and menu/search/input alignment. The complete category-by-category record—including removed development experiments and all 18 languages—is maintained in [CHANGELOG-COMMUNITY.md](CHANGELOG-COMMUNITY.md).

## More details

- [Cumulative Community changelog](CHANGELOG-COMMUNITY.md)
- Maintainer's private release checklist
- Version information is provided by the final release manifest
- [Official downloads](https://github.com/dutu-dev/TuffNode-Community/releases)
