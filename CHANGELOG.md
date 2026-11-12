# TuffNode Community Changelog

Public release history is listed here. The v1.5.0 release preparation branch contains the cumulative entry since v1.0.1; the public main branch remains on v1.0.1 until publication.

> v0.7.6 consolidates the Community work delivered since the v0.6.0 public release. Intermediate development milestones are intentionally folded into this release entry.

---

## v1.5.0 — Next public release (cumulative since v1.0.1)

**Release:** TuffNode Community v1.5.0  
**Previous public stable release:** v1.0.1 — 27 October 2026  
**Scope:** all changes since v1.0.1. Versions 1.0.2–1.4.x were internal development/testing builds, not public stable releases.  
**Product:** Local-first Windows x64 Minecraft server management.

TuffNode Community v1.5.0 consolidates the development work after v1.0.1 into a single public update: player inventories and Chat, TPS monitoring, better console/add-on/backup management, expanded protection and security updates, 18-language localization, refreshed desktop UX, and installer/privacy improvements.

### 1. Server Management

- Refined the Home dashboard and Recent Servers presentation.
- Improved server ordering based on recent activity.
- Improved the Servers table with creation-date sorting, filtering and search.
- Refined server status indicators for starting, loading, online, stopping, stopped and failed states.
- Improved Start, Stop and Restart controls and their visual feedback.
- Improved Java process detection and server shutdown handling.
- Refined server creation and import dialogs.
- Improved server configuration editing and save operations.
- Improved workspace navigation and handling of unsaved settings.
- Improved support for managed and imported server configurations.
- Added direct access to the official Minecraft EULA during server creation; opening the terms does not accept them.
- Standardized server management action buttons, spacing and alignment.
- Improved server startup and failure notifications without treating routine tick lag as a crash.
- Improved responsiveness of modal forms and server configuration editors.

### 2. Monitoring and Performance

- Added live TPS monitoring for compatible Minecraft server implementations.
- Implemented shared TPS sampling using the server's `tps` command.
- Configured sampling approximately every 10 seconds.
- Shared TPS results between supported dashboard views to avoid redundant polling.
- Added TPS information to Home, Servers, Network and server overview.
- Added explicit unavailable states for unsupported or offline servers; TPS is never inferred from CPU usage.
- Improved CPU, RAM, PID and uptime presentation.
- Removed redundant PID information from selected dashboards.
- Standardized resource value typography and numeric alignment.
- Aligned CPU, RAM and TPS labels and values using consistent grid columns.
- Improved server process discovery and monitoring reliability.
- Refined global and per-server Network status cards, public/local IP address presentation, copy icons and tooltips.
- Moved Refresh Addresses slightly higher in Server → Network, placing the loading indicator in its own row to avoid overlap.
- Improved public-IP and port diagnostic response validation.
- Removed experimental inbound/outbound network traffic monitoring and its background collectors; this feature does not ship in v1.5.0.

### 3. Player Management

- Added expanded player detail inspection.
- Added live player inventory inspection where supported, using captured server responses.
- Added saved-playerdata fallback for unavailable live data.
- Added Ender Chest inspection.
- Added Bundle content inspection.
- Added Shulker Box inspection.
- Added support for nested inventory containers.
- Improved item slot ordering and inventory layouts.
- Improved handling of non-stackable items and empty containers.
- Expanded item tooltips and available item metadata, including durability information where available.
- Added locally cached Minecraft item assets with improved offline handling.
- Improved inventory loading and error feedback.
- Improved player searches, filters and management controls.
- Refined player detail timestamps, refresh controls, scrollbars and modal presentation.
- Hardened NBT/SNBT data parsing, decompression limits and nested inventory limits.
- Removed the external MCHeads player-image integration and associated third-party image requests.

### 4. New Chat Workspace

- Introduced a dedicated Chat tab.
- Separated recognized Minecraft player chat from diagnostic console messages.
- Added conversation-style message bubbles.
- Added player names, avatar initials and timestamps.
- Added visually distinct outgoing server messages.
- Added message composition through the Minecraft `say` command.
- Added Enter-to-send functionality.
- Added automatic scrolling for incoming messages.
- Added per-server conversation history during the current application session.
- Preserved unsent drafts across tab and server navigation.
- Added a Clear action and bounded message retention.
- Renamed In-game Chat to Chat consistently across the workspace and all supported locales.
- Chat uses recognized Minecraft console message formats; third-party plugin formats may require additional parser support.
- Chat history is not a persistent messaging archive and is not guaranteed to survive application restart.

### 5. Console Improvements

- Improved console command autocomplete.
- Added context-aware command argument suggestions.
- Improved online player and known-player suggestions.
- Improved Minecraft selector completion.
- Improved command input keyboard navigation.
- Improved Tab completion and suggestion selection.
- Refined console command history and input feedback.
- Improved text wrapping and command presentation.
- Refined console control spacing and loading states.
- Improved safe handling of command response capture used by live player information and TPS sampling.

### 6. Add-ons Management

- Improved catalog browsing and incremental loading.
- Refined lazy loading and result virtualization.
- Improved add-on search and filtering controls.
- Improved icon downloading, caching, size limits and rendering.
- Added more resilient local icon handling.
- Improved installed add-on metadata and display names.
- Redesigned add-on detail dialogs.
- Redesigned installed add-on details and action placement.
- Improved installation and download progress indicators.
- Improved installed-state visibility and version status.
- Refined download, installation and update feedback.
- Improved alignment of search bars, toolbars, headers and list rows.
- Strengthened archive validation and installation rollback behavior.
- Improved prevention of unsafe paths, case-colliding and duplicate archive entries.
- Refined anti-cheat suggestion and dismissal behavior.

### 7. Backups, Restore and File Management

- Added stronger backup integrity verification, including SHA-256 mechanisms.
- Improved ZIP archive structural validation.
- Strengthened CRC32 verification and decompressed-data checks.
- Improved archive traversal protection.
- Added additional safeguards against unsafe filesystem destinations, Windows-reserved paths and junction/reparse-point escapes.
- Improved backup creation, restore and add-on operation coordination.
- Improved handling of malformed or oversized backup archives.
- Added protection for sensitive server configuration values in sanitized backup snapshots; RCON passwords are redacted unless explicitly included.
- Improved backup refresh and scrolling behavior.
- Improved backup loading indicators and error messages.
- Refined backup configuration controls and confirmation dialogs.
- Improved File Manager navigation, actions and loading feedback.
- Improved configuration editor limits and presentation.
- Community continues to use standard portable ZIP backups: experimental mandatory application encryption, Windows EFS and recovery-password approaches were removed during development.
- Exported backup archives remain the server operator's responsibility to protect.

### 8. Security and Protection

- Introduced a dedicated Security Updates interface, replacing the user-facing Shield navigation name with Security while retaining Shield controls.
- Added a signed security-patch distribution workflow.
- Added patch manifest verification against the pinned publisher key.
- Added package checksum, size, sequence and compatibility validation.
- Added staged patch downloads.
- Required explicit user approval before applying a security patch; patch discovery/download may be automatic.
- Introduced a separate patch installation helper.
- Added maintenance progress reporting.
- Added transactional patch application and rollback mechanisms.
- Added recovery handling for interrupted installations.
- Improved patch archive and destination validation.
- Expanded the presentation and configuration of the three Shield protection layers.
- Improved server-side Shield plugin integration for compatible servers.
- Improved trusted and blocked IP management.
- Added temporary blocking and login-abuse protection controls.
- Improved Windows Firewall rule synchronization, including TCP/UDP endpoints where relevant.
- Strengthened ownership-aware Minecraft ban management.
- Added persistent local Shield security audit information.
- Improved notifications for protection failures and recovery.
- Strengthened HTTPS download policies.
- Added additional redirect, hostname, port, DNS and public-target-address validation.
- Improved protections against SSRF, DNS rebinding and HTTPS-to-HTTP downgrade.
- Restricted unsafe private, reserved and loopback network destinations.
- Added bounded handling for external HTTP response content.
- Improved archive extraction limits and unsafe-path detection.
- Improved sensitive-data redaction in diagnostic and application logs.
- Hardened Minecraft player-name validation before administrative commands.
- Expanded security regression tests and dependency vulnerability checks.
- These measures reduce known risks but do not guarantee zero vulnerabilities.

### 9. Network Improvements

- Redesigned network status and address presentation.
- Improved local and public connection address visibility.
- Standardized copy-address buttons.
- Added contextual network explanations and tooltips.
- Improved diagnostic loading indicators.
- Improved public-IP and port-check response handling.
- Improved alignment of managed server counters and connection information.
- Refined Server → Network, including Refresh Addresses positioning and a dedicated loading-bar row.
- Removed the experimental background network traffic monitor.
- Hardened external provider HTTPS, redirect and public-IP connection handling.

### 10. Notifications and Reliability

- Added improved alerts for unexpected server failures.
- Added scheduled-backup failure notifications.
- Added notifications for available server software updates.
- Added warnings for low available disk space on server volumes.
- Improved notification deduplication.
- Refined notification flyout behavior.
- Improved unread notification badge positioning.
- Added themed notification detail overlays.
- Improved outside-click dismissal and Silent Mode interactions.
- Refined system tray menus and exit confirmations.
- Replaced additional native Windows dialogs with themed application dialogs.
- Improved loading states for asynchronous operations.
- Improved operational error reporting and handling of unavailable resources.

### 11. Appearance and UI/UX

- Added Catppuccin Mocha, Tokyo Night, Nord Arctic, Dracula and Rosé Pine Dawn themes.
- Refined window chrome and rounded corners.
- Improved maximized-window boundaries and taskbar integration.
- Standardized page margins and content spacing.
- Standardized buttons, toggles, icons and interactive states.
- Improved mouse hover and button press animations.
- Improved keyboard-only focus indicators.
- Refined modal overlays and theme-dependent backdrop behavior.
- Improved loading bar shapes and positioning.
- Corrected clipping in toolbars, search controls and window edges.
- Improved text field and placeholder alignment.
- Refined typography across dashboards and management pages.
- Improved Home, Servers, Network, Players, Add-ons, Files, Logs and Settings layouts.
- Standardized table-header and data-column alignment.
- Refined close-button hover contrast and destructive-action styling.
- Improved visual behavior when changing themes.
- Corrected several theme brush and overlay rendering issues.
- Standardized Home/Servers header actions and CPU/RAM/TPS resource columns.
- Gruvbox was evaluated during development but removed from the final theme selection.

### 12. Localization

- Updated localization resources for English, Romanian, German, Spanish, French, Italian, Brazilian Portuguese, Dutch, Polish, Czech, Hungarian, Swedish, Turkish, Russian, Ukrainian, Japanese, Korean and Simplified Chinese.
- Updated translations for Chat and Security.
- Expanded translations throughout server management.
- Updated player, inventory and backup interfaces.
- Updated Add-ons and Network terminology.
- Expanded settings, errors and notification translations.
- Improved translated confirmations and interface labels.
- Added localization consistency tools.
- Aligned translation resource structures across all supported languages.
- All 18 locale files contain the same 1,079 resource keys as English; structural coverage was checked, but language quality requires separate review.

### 13. Privacy and Local Data Controls

- Added clearer player-history retention settings.
- Improved local player-history cleanup.
- Added application log cleanup controls.
- Improved handling of selected third-party network requests.
- Consolidated privacy information around the public Privacy & Responsible Use Notice at https://tuffnode.com/privacy.
- Updated installer acknowledgement requirements.
- Removed the external MCHeads player-image integration and associated requests.
- Updated documentation to reflect the application's actual data-handling behavior.
- Displayed the complete Privacy & Responsible Use Notice during installation, with its last updated date and explicit acknowledgement.

### 14. Installer and Release Engineering

- Updated application versioning to v1.5.0.
- Aligned application, PatchRunner, installer and release metadata.
- Prepared the .NET 10 Windows x64 publishing workflow.
- Added explicit PatchRunner publishing to the expected packaged output directory.
- Preserved the existing Community installation identity for in-place upgrades.
- Updated the installer license and privacy acknowledgement flow.
- Updated installer descriptions and release documentation.
- Included the complete cumulative release changelog and versioned release notes in the installer.
- Prepared optional Authenticode signing.
- Added SHA-256 checksum generation and verification.
- Added a structured release manifest.
- Improved installer preflight validation, including the canonical changelog and privacy notice.
- Expanded the release checklist and public GitHub release documentation.
- GitHub Actions is optional for this release; the release is validated locally by its maintainer.

### 15. Important Compatibility Notes

- TuffNode Community remains a local desktop Minecraft server management application.
- Direct Connect and Core-only remote features are not included.
- TPS depends on compatible Minecraft server output.
- Live inventory information depends on server capabilities and available player data.
- Chat relies on supported Minecraft log formats.
- Chat message history is session-scoped, not a synchronized or persistent messaging service.
- Backup archives remain portable ZIP files; no built-in end-to-end backup encryption is promised.
- External Minecraft software, plugins, mods and services remain subject to their own licenses and terms.
- Supported Windows x64 versions must follow the .NET 10 and installer compatibility requirements.

### Release Summary

TuffNode Community v1.5.0 combines the improvements developed after v1.0.1 into one substantial public update. The objective is to make Community more capable, consistent, reliable and secure while preserving its local-first approach to Minecraft server management.

For complementary details, see [v1.5.0 release notes](RELEASE-NOTES-v1.5.0.md). The 15 sections above are the authoritative cumulative v1.5.0 change list; the website and installer must use this same list.

---

## v1.0.1 — 2026-10-27 — Patch release

### Fixed

- Improved backup-content checkbox visibility across themes.
- Added a clear checked-state indicator with stronger contrast, visible borders and hover feedback.
- Made selected and unselected backup folders easier to distinguish, including BlueMap data.

This patch addresses the visual feedback reported after the v1.0.0 release.

---

## v1.0.0 — 2026-10-26 — Stable release

TuffNode Community v1.0.0 is the first stable Community release after the 0.7.x development cycle.

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
- Disabled Start and Restart while an update transaction is active.
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

### Release bundle

- `TuffNode-Community-v1.0.0.exe`
- `TuffNode-Community-v1.0.0.exe.sha256`
- `checksums.txt`
- `TuffNode-Community-v1.0.0.release.json`

The installer preserves the existing Community AppId for in-place upgrades from 0.7.6.

---

## v0.7.6 — 2026-10-03 — Released

### Runtime and JVM

- Added managed Auto, G1GC, ZGC and Shenandoah profiles with one shared launch policy.

- Added JVM launch preview, structured arguments and editable advanced JVM arguments.

- Centralized CPU/RAM telemetry and bounded Java child-process discovery for script launches.

- Added live PID, CPU, memory and uptime information for the Minecraft process.

### Servers, lifecycle and configuration

- Rebuilt the server catalogue reconciliation to prevent duplicate, ghost and disappearing rows.

- Added safer imported-server handling and synchronization of external server.properties changes.

- Added provider-aware configuration discovery and rollback-consistent visual/raw saves.

- Added coordinated server relocation with managed filesystem ownership and rollback.

- Added single-instance protection and safer shutdown behavior.

### Networking and security

- Added public TCP reachability checks with listener, firewall and NAT/CGNAT explanations.

- Added cached, deduplicated and stale-result-safe network probes.

- Hardened managed paths against junction/symlink escapes.

- Preserved Community product boundaries without importing Core-only remote features.

### Add-ons

- Hardened Modrinth, Hangar and Spigot downloads with trusted HTTPS hosts, redirect validation and bounded payloads.

- Added strict JAR/ZIP validation, local datapack import and atomic installs.

- Added rollback-safe tracked updates with provider, project, version and SHA-256 metadata.

- Added a virtualized catalog with improved thumbnails, installed-state tracking and title/JAR metadata.

- Reworked details into a true modal with a transparent blurred backdrop.

- Added compatible version enumeration and exact-version installation.

### Backups and reliability

- Serialized backup create, restore and delete operations.

- Added restore validation, disk-capacity checks and rollback-staging cleanup.

- Added backup presets with granular include/exclude checkboxes; manual edits switch the preset to Custom.

- Protected unsaved configuration when switching servers or workspaces.

- Suspended hidden metrics pages and reduced unnecessary UI churn.

### UI and desktop polish

- Added high-DPI layout rounding, consistent typography and responsive card layouts.

- Removed the local-address column from Servers so action buttons keep stable space without horizontal scrolling.

- Standardized action button dimensions, spacing, alignment and hover feedback.

- Added consistent Fluent icons for System and Appearance.

- Added subtle hover-scale motion to shared buttons and workspace tabs.

- Preserved runtime themes, accent colors, notifications, tray/taskbar states and offline localization.

### Release integrity

- Centralized v0.7.6 versioning across application and installer.

- Added fail-closed installer preflight for version, publisher, license, release notes and executable metadata.

- Added SHA-256 checksums and release-manifest support.

- Preserved the existing Community AppId for in-place upgrades.


---

## v0.6.0 — 2026-09-10

v0.6.0 is the final UI, stability, desktop-integration and power-user polish release built on top of the modular v0.5.0 architecture.

### Highlights

- Rebuilt the desktop shell into a denser administration-focused experience.
- Added full runtime theme switching with semantic dynamic-resource tokens.
- Added dark and light palettes, including Snow, Porcelain and Daylight.
- Added runtime accent switching for primary actions, including Amber, Emerald, Cyan, Indigo and Rose.
- Added the centralized Notification Center with unread state, severity levels, history and Silent Mode.
- Added Windows System Tray integration with idle, running and alert branding states.
- Added dynamic System Tray and Windows Taskbar telemetry/tooltips.
- Added official TuffNode application, installer and tray branding assets.
- Added Start with Windows support through the current-user Registry Run key.
- Added configurable window-close behavior:
  - Minimize to System Tray;
  - Exit Application with safe server shutdown confirmation.
- Added full localization support across 18 bundled offline languages.

### Server creation

- Rebuilt Create Server into a fixed three-row modal:
  - fixed header;
  - scrollable configuration body;
  - fixed action footer.
- Restored Geyser / Bedrock Support inside the scrollable creation flow.
- Added server icon selection and managed 64 × 64 PNG processing.
- Added smart server-port selection:
  - prefer 25565;
  - fall back to a free dynamic port when needed.
- Added Java runtime selection and automatic Eclipse Temurin provisioning.
- Added separate minimum and maximum RAM controls.
- RAM allocation is bounded by **total physical RAM**, not momentary free RAM.
- Creating a server with more RAM than is currently free is allowed and produces only an informational warning.
- Hardened duplicate-create protection so a rapid/double Create action cannot provision the same request twice.

### Servers Hub and persistence

- Rebuilt Servers into a dense searchable/filterable table.
- Increased default window size to 1240 × 760 with a supported 1024 × 640 minimum.
- Redesigned row actions:
  - Start as the primary accent action;
  - Open folder as a secondary action;
  - Delete as a destructive action.
- Fixed the critical bug where starting one server could make other servers disappear from the All filter.
- Fixed server catalogue race conditions by reconciling repository snapshots instead of clearing/rebuilding the UI collection.
- Added defensive deduplication by server ID and normalized physical directory.
- Fixed a WPF `ListCollectionView` first-load race that could temporarily display the same server row twice until the next refresh.
- Fixed first-navigation list flicker/ghost rows.
- Kept `IServerRepository/ListAsync` as the authoritative catalogue source.
- External `server.properties` changes now synchronize operational metadata such as `server-port` back into TuffNode.
- Import/reconnect/reload flows now pick up externally changed server ports and refresh the UI.

### Workspace and administration

- Reworked server settings and provider-aware configuration editing.
- Added provider-aware raw configuration discovery for Paper, Purpur, Spigot/CraftBukkit, Fabric, Forge and NeoForge.
- Added safer visual/raw `server.properties` synchronization.
- Added live per-server process telemetry:
  - PID;
  - CPU;
  - memory.
- Added live player telemetry.
- Rebuilt Add-ons around Catalog and Installed workflows.
- Added local plugin/mod management.
- Added the optional deterministic anticheat scanner and Grim recommendation flow.
- Preserved modular Overview, Console, Players, Add-ons, Backups, Config and Files workspaces.
- Improved backup scheduling and compact-window behavior.

### Notifications and desktop integration

- Added `INotificationService` and persistent notification history.
- Notification history is capped at 150 items.
- Added Mark all as read, Clear all and Silent Mode.
- Added notifications for:
  - backup success/failure;
  - unexpected server exits;
  - Shield enable/disable.
- Fixed the notification-bell popup toggle race that caused the panel to reopen immediately when clicking the bell to close it.
- Added taskbar overlay states for active and failed servers.
- Added dynamic Taskbar and System Tray tooltip text.
- Added the official app icon to the executable, window and title bar.
- Added official idle/running/alert tray icons.
- Added “Report bugs or give feedback” above the support email in the sidebar footer.

### Themes and visual stability

- Replaced partial theme mutation with a strict semantic token contract.
- Converted theme-dependent colors to `DynamicResource` bindings.
- Added global theme-aware styles for TextBox, ComboBox, ComboBoxItem, CheckBox and Slider.
- Fixed light-theme contrast across the entire shell, sidebar, inputs, cards and dropdowns.
- Fixed XAML binding diagnostics caused by invalid FocusManager element bindings.
- Replaced nullable string-to-`ImageSource` bindings with typed image properties.
- Added CI guards for dynamic theme tokens and unsafe WPF bindings.

### Reliability and error handling

- Added an application-wide exception boundary for UI, async-command and background-task failures.
- Added guarded fire-and-forget execution paths across runtime, tray, add-ons, Shield and loaded-view operations.
- Added user-facing error dialogs for recoverable destructive-operation failures.
- Hardened server deletion when Java/JAR files remain temporarily locked.
- Added retry handling for locked-file directory deletion.
- Fatal runtime conditions remain fatal instead of being incorrectly swallowed.
- Error details are written to the TuffNode local application log.

### Build and validation

- Windows / .NET 10 CI builds with warnings treated as errors.
- **0 warnings**
- **0 errors**
- **69 / 69 tests passing**
- Release head: `d5b439d103c65126f5380781fd40115495a2d6f5`

---

## v0.5.0 — 2026-09-08

v0.5.0 was the major Community architecture and UI milestone. It replaced the legacy server-management monolith with dedicated feature ViewModels and introduced the offline localization engine.

### Architecture

- Split the server workspace into dedicated modules:
  - Overview;
  - Console;
  - Players;
  - Add-ons;
  - Backups;
  - Config;
  - Files.
- Reduced `ServerWorkspaceViewModel` to orchestration/shared workspace responsibilities.
- Removed obsolete `ServerDetailsViewModel` and `ContentBrowserViewModel` after migration.
- Preserved the existing runtime/services instead of duplicating domain behavior in UI layers.

### Servers and workspace redesign

- Rebuilt the server workspace around compact tabs and dense administration controls.
- Rebuilt Servers as a searchable/filterable server catalogue.
- Added compact Create and Import flows.
- Added dedicated per-server Network and Shield surfaces.
- Added breadcrumb-based file navigation.
- Expanded player administration and add-on workflows.
- Moved backup and configuration behavior into dedicated modules.
- Standardized technical values on monospaced/tabular typography.

### Localization

- Added the embedded JSON localization engine.
- Added WPF `{loc:Tr ...}` markup-extension support.
- Added live language switching.
- Bundled 18 offline locales:
  `en`, `ro`, `de`, `es`, `pt-BR`, `fr`, `pl`, `it`, `nl`, `cs`, `hu`, `sv`, `tr`, `uk`, `ru`, `ja`, `ko`, `zh-CN`.
- Added strict selected-language → English → diagnostic-key fallback behavior.

### Safety and quality

- Added `AtomicFileStorage` and safer configuration/file workflows.
- Extended safe server-path validation.
- Added keyboard/focus polish for power-user workflows.
- Kept the solution under Windows/.NET 10 warnings-as-errors CI.
- Final milestone commit: `7eadb2bc3f36b9452923fc526013768c813f9a22`

---

## v0.4.2 — 2026-09-08

v0.4.2 was the stabilization milestone immediately before the modular v0.5.0 rebuild.

### Reliability and persistence

- Added the shared `SafeServerPath` validation layer.
- Hardened managed/imported server path handling.
- Added `AtomicJsonStorage` with safer write/replace behavior and corrupt-file recovery.
- Hardened `AsyncRelayCommand` execution boundaries.
- Reduced duplicated/unobserved async UI operations.

### Backups and scheduler

- Hardened live backup creation.
- Improved snapshot/restore path safety.
- Reworked backup scheduler lifecycle management.
- Reduced scheduler state races and duplicate background work.

### Shield and runtime

- Added shared Shield policy semantics.
- Hardened Windows Shield behavior and runtime readiness handling.
- Improved server startup/readiness transitions.
- Improved server library/import path handling.

### CI and tests

- Added the `TuffNode.Core.Tests` project.
- Added Windows test execution to CI.
- Added regression coverage for safe paths, atomic JSON and Shield semantics.
- Stabilization integration commit: `e6432ea00d238b1c60811ae4dd92ed31898a9b44`

---

## v0.4.1 — 2026-08-30

v0.4.1 focused on server lifecycle safety, add-on management, networking clarity and Community release polish.

### Server management

- Added a complete managed-server deletion flow.
- Added Delete directly to server rows and the Manage view.
- Added destructive confirmation before managed-server deletion.
- Imported servers use a safe Remove from TuffNode flow that preserves their original files.
- Active servers are stopped before deletion/removal.
- Fixed stale server rows after deletion.

### Add-ons

- Added installed add-on management.
- Added enable, disable and uninstall actions.
- Added Enter-to-search behavior.
- Improved the Community content installer flow.

### Geyser, Network and Shield

- Improved Geyser/Bedrock connection information.
- Displayed Bedrock UDP endpoints alongside related Java connection information.
- Clarified Shield protection refresh behavior.
- Improved server settings apply/restart messaging.

### Installer and release polish

- Bumped Community to v0.4.1.
- Kept the existing Community installer AppId for in-place upgrades.
- Updated final application/installer icons.
- Set Community publisher metadata to Dutu.
- Added optional release code signing.
- Fixed Desktop shortcut creation.
- Standardized installer output as `TuffNode-Community-v0.4.1.exe`.
- Version bump commit: `d36e6ee68ce5383af4abef6fa0712f9736dae58d`

---

## v0.4.0 — 2026-08-29

v0.4.0 was the first major Community rebuild after the original preview line.

### Community shell and server-first UX

- Rebuilt the application shell around the Community navigation model.
- Introduced the server-first Home experience and rebuilt Manage workspace.
- Added selected-server state across Home and Servers.
- Added reusable Create Server and Import Server overlays.
- Added richer application/version/build metadata in the footer.
- Refined the Community visual language and dark palette.

### Server creation and runtime

- Added server icon selection and replacement.
- Added minimum/maximum heap controls and JVM presets.
- Added managed Java selection during server setup.
- Added improved startup lifecycle states and readiness handling.
- Preserved console history across workspace reloads.
- Added direct console command submission with Enter.

### Add-ons and content

- Added local plugin/mod installation.
- Added richer add-on browsing and installed-content views.
- Added Spigot resource browsing through Spiget.
- Added download/archive validation before installation.

### Backups

- Added configurable backup root paths.
- Added backup-folder controls.
- Expanded backup scheduler configuration and UI.

### Network, Shield and TuffNode services

- Added Minecraft-level Shield IP enforcement fallback when Windows Firewall is unavailable.
- Added runtime reapplication of Shield IP blocks.
- Introduced the TuffNode Sync publishing terminology and persisted state.
- Added managed Geyser installation and Bedrock support to server creation/workspace.
- Added runtime and Bedrock settings in the server workspace.

### Installer

- Bumped Community to v0.4.0.
- Added the Inno Setup Community installer workflow.
- Added deterministic app/build version metadata.
- Prepared the one-command Community installer build.
- Version bump commit: `a15ef6e9e2ab1d51dbb5c27d92735d1c1706f467`

---

## v0.1.0-beta — 2026-08-24

The first public TuffNode Community Preview.

### Foundation

- Added the Windows WPF application shell and MVVM navigation foundation.
- Added host/system resource monitoring.
- Added managed Java runtime discovery and installation.
- Added provider-aware server creation.

### Minecraft providers

Initial provider support included:

- Vanilla;
- Paper;
- Purpur;
- Fabric;
- Forge;
- NeoForge;
- Spigot;
- CraftBukkit.

TuffNode handled provider-specific artifacts and Java/JDK requirements.

### Server administration

- Added server runtime management.
- Added live console output and commands.
- Added server details and `server.properties` configuration.
- Added provider-aware raw config editing.
- Added server rename/update and deletion flows.
- Added server logs.
- Added backup creation/configuration.
- Added server file browsing.
- Added installed plugin discovery.
- Added live player discovery through the running server.

### Preview shell and installer

- Added the first Community application shell.
- Added early Guided/Advanced experience-mode foundations.
- Added application version information and preview branding.
- Added the Community Preview installer.
- Public preview tag: `v0.1.0-beta`
- Tagged commit: `7a4306eac2bba25dac018b54c976eb3101203bec`

---

## Version timeline

| Version | Date | Type |
| --- | --- | --- |
| **v0.6.0** | 2026-09-10 | Community release |
| **v0.5.0** | 2026-09-08 | Community architecture milestone |
| **v0.4.2** | 2026-09-08 | Stabilization milestone |
| **v0.4.1** | 2026-08-30 | Community release |
| **v0.4.0** | 2026-08-29 | Community rebuild release |
| **v0.1.0-beta** | 2026-08-24 | First public preview |
