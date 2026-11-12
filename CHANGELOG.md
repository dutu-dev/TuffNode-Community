# TuffNode Community Changelog

Public release history is listed here. The v1.5.0 release preparation branch contains the cumulative entry since v1.0.1; the public main branch remains on v1.0.1 until publication.

> v0.7.6 consolidates the Community work delivered since the v0.6.0 public release. Intermediate development milestones are intentionally folded into this release entry.

---

## v1.5.0 — Cumulative update since public v1.0.1

**Comparison baseline:** TuffNode Community **v1.0.1**, published **27 October 2026**.  
**Scope:** the complete cumulative change set to v1.5.0; intermediary 1.0.2–1.4.x builds were **internal development milestones, not public stable releases**.  
**Source review:** 1,600 development commits and 228 changed files relative to the development commit preparing v1.0.1, plus public-distribution metadata reviewed against the released v1.0.1.

### Server library, navigation and lifecycle

- Refined Home/Recent Servers with more consistent server rows, status information, action placement and recent-activity ordering.
- Refined the Servers table, search, server-creation date sorting, labels, controls and responsive row actions.
- Improved server lifecycle status presentation across starting, loading, online, stopping, failed and stopped states.
- Improved startup/failure reporting and operational notifications; ordinary lag is not treated as a server-crash alert.
- Improved handling of Java process discovery and orphaned processes; strengthened normal shutdown lifecycle.
- Refined server workspace navigation, tab toolbars, status counters, notification interactions and unsaved-configuration protections.
- Improved creation/import dialog sizing, scrollbar behavior, JVM preset alignment and layout on smaller windows.
- Added direct access to the official Minecraft EULA from the server-creation agreement control; opening the terms does not automatically accept them.
- Refined server settings, including managed Java/runtime settings and save interactions for server properties.
- Improved configuration-editing presentation, including line alignment, bounded content and consistent themed dialogs.

### Runtime monitoring and Network

- Added **TPS monitoring** to supported server dashboards, including server overview, Home, Servers and Network status displays.
- TPS is sampled at an approximately **10-second** cadence using a captured `tps` console command; samples are shared across views to avoid duplicate polling.
- TPS shows `—` when the server is stopped, the command is unsupported or valid command output is unavailable; the value is **not inferred from CPU usage**.
- Reorganized displayed server metrics and removed redundant PID presentations while keeping live process CPU, RAM, PID and uptime where relevant.
- Improved CPU/RAM/TPS row alignment using separate label/value columns, tabular numerals and uniform spacing.
- Refined per-server Network cards, including local/public address presentation, copy icons, descriptions and status/tooltips.
- Adjusted the **Refresh Addresses** button in the **server's Network tab** and separated its loading indicator to avoid overlap.
- Refined the global Network page with clearer server-status, local/public address and action columns, aligned counters and progress feedback.
- Strengthened manual public-IP/port diagnostic handling and timeout/retry response safety.
- Removed experimental persistent inbound/outbound network traffic monitoring and its background collectors; this is **not a v1.5.0 feature**.

### Player details, inventories and gameplay information

- Added richer per-player details, including available gameplay/inventory information and snapshot timestamps.
- Added **live Minecraft player inventory inspection** using captured server command output when supported; retained an explicit saved-playerdata fallback when live inspection is unavailable.
- Added saved Ender Chest inspection and recursive support for **Bundles** and **Shulker Boxes**, including nested containers and slot ordering.
- Improved support for non-stackable items, empty containers, item quantities, item durability descriptions and hover details.
- Added locally cached official Minecraft item visual assets, with bounded decoding, download size checks and better offline behavior.
- Hardened NBT/SNBT parsing, decompression and nested inventory limits to avoid oversized or malformed payloads.
- Improved the player-detail modal: metadata/Refresh alignment, available scroll width, compact controls and visual consistency.
- Refined player search, filters, action sizing, table headers, counts and empty-state explanations.
- Removed the external MCHeads/player-head image integration and associated remote image requests; the interface no longer depends on that image service.

### Dedicated Chat tab and Console

- Introduced a dedicated **Chat** workspace, separate from raw server-console and operational logging.
- Displays recognized standard Minecraft player chat in conversation bubbles, with avatar initials, author, time and message content.
- Shows TuffNode-sent server messages separately, with right-aligned outgoing bubbles.
- Added a fixed composer with **Enter** and Send actions using Minecraft's `say` command.
- Preserves recent messages and unsent drafts **per server in memory** across tab/server navigation; includes Clear and bounded history.
- Does not persist a permanent chat archive; third-party chat plugin formats may require additional parsing.
- Improved console command autocompletion with command arguments, valid selectors, available online players, known/offline targets where appropriate and block/item context.
- Improved console suggestion navigation and accepted-value insertion, keyboard handling and command history.
- Improved console text wrapping, input controls and layout stability.

### Add-ons and installed content

- Refined catalog discovery and loading, including lazy loading, virtualization and incremental result presentation.
- Improved add-on catalog icon loading, caching/downscaling, supported image decoding and bounded cache memory.
- Refined installed add-on information, display-name metadata, installed-state tracking and version status display.
- Redesigned catalog and installed add-on details dialogs, including layout, actions, location labels, progress feedback and visual hierarchy.
- Improved add-on download/install busy indicators, button states, toolbar height and horizontal overflow behavior.
- Improved search text/placeholder alignment, bottom-toolbar clearance, installed-list header alignment and scroll behavior.
- Strengthened archive validation, destination confinement, duplicate-file/colliding-path handling and recovery after failed content updates.
- Refined anti-cheat suggestion dismissal persistence and compatible add-on administration flows.

### Backup, restore, files and configuration

- Strengthened backup archive verification, including **SHA-256 integrity handling**, ZIP structural/integrity checks and CRC32 checks against decompressed content.
- Added stronger path traversal, invalid entry name, reparse-point/junction, archive expansion and filesystem containment safeguards.
- Improved backup and add-on operation sequencing and per-server mutation coordination.
- Added protection for backed-up server configuration secrets, including RCON password redaction unless deliberately included.
- Improved backup list refresh, scroll retention, focus control, loading and restore feedback.
- Refined backup dialogs, confirmation overlays, responsive toolbar controls and empty states.
- Improved File Manager navigation, download states, selection and action-button alignment.
- Maintained **standard portable ZIP backups**. Experimental application encryption / EFS / recovery-password backup variants introduced during development were **removed**; users must secure exported backup files themselves.

### Security: protection and updates

- Expanded the optional Shield protection configuration with clearer **three-layer** defense status, settings and explanations.
- Added/synchronized an optional server-side TuffNode Shield Bukkit plugin and its managed local installation workflow for compatible servers.
- Added handling for temporary blocks, trusted/blocked addresses, login-abuse detection and Windows Firewall TCP/UDP endpoint policies.
- Improved Shield policy reconciliation, ownership-aware Minecraft bans and avoidance of interfering with operator-managed bans.
- Added durable local Shield security audit events and rate-limit/persistence safeguards.
- Improved notices for degraded/restored enforcement and missing/returning server-side plugin components.
- Renamed the primary user-facing **Shield** navigation area to **Security** while retaining underlying Shield protection capabilities.
- Introduced a signed security-patch update channel, backed by the public security updates repository, with pinned publisher verification, compatible manifest/payload checks and staged downloads.
- Added **explicit approval before applying security patches**; patch discovery/download may run automatically, but installation is not silently forced.
- Added a separate patch runner, in-app/maintenance-window progress, transaction journal, verified backups, rollback and recovery after interruption.
- Tightened accepted signed patch identifiers, versions, asset names, declared file operations, archive size and safe extraction targets.

### Network, download and parsing hardening

- Enforced secure HTTPS-oriented external provider communication and explicit validation of allowed hosts, redirects, ports, public IP targets and DNS results.
- Strengthened protections against SSRF, private/loopback/reserved IP routing, DNS rebinding and HTTPS-to-HTTP downgrade.
- Added bounded HTTP response readers for external provider metadata, catalogs, Minecraft version information and network diagnostics.
- Hardened server software, Java runtime, add-on and security-patch download handling with size/hash checks where provided.
- Strengthened ZIP/JAR path and metadata parsing, Windows reserved names, collision checks and expanded-size enforcement.
- Added more comprehensive secret redaction for diagnostic/application logs, webhook and signed-URL credentials.
- Centralized Minecraft player-name validation before generating privileged administration commands.
- Updated security-sensitive dependencies and added/expanded automated regression tests, NuGet vulnerability auditing and CodeQL/OSV scanning configuration.
- Security controls reduce known risks; **they do not constitute a guarantee of zero vulnerabilities**.

### Notifications and operational reliability

- Added notifications for server faults, failed scheduled backups and available server software updates.
- Added warnings when free space on the volume containing a managed Minecraft server becomes low.
- Improved deduplication of repeated operational alerts and severity/status text.
- Refined notification flyout behavior, unread badge alignment, outside-click dismissal, Silent Mode interactions and detailed notification overlays.
- Replaced more native Windows message boxes with themed TuffNode dialogs, including consistent confirmations and full-window dimming.
- Refined system tray context menus and exit confirmations to follow the app's visual theme.
- Added more consistent busy/progress states and cancellation handling for long-running operations.

### Design, themes, UX and Windows integration

- Added **Catppuccin Mocha, Tokyo Night, Nord Arctic, Dracula and Rosé Pine Dawn** appearance themes.
- Stabilized dynamic theme brushes, background/surface colors, overlay/backdrop opacity and theme-change rollback behavior.
- **Gruvbox was trialed and then removed**; it is not listed as a shipped theme.
- Refined titlebar, window chrome, rounded normal-window corners, maximized work area, keyboard focus feedback, resizable layouts and system tray styling.
- Standardized margins, page headers, shared section spacing, form controls, button dimensions, icon sizes and hover/press animations.
- Improved Home, Servers, Java, Network, Settings, Security, Players, Backups, Add-ons, Logs and Files alignments.
- Fixed clipping/overflow in searches, dropdowns, toolbar buttons, scrollbars, bottom content edges and dense cards.
- Standardized server overview metric typography and technical-text presentation; improved truncation, word wrapping and table-header/value baselines.
- Adjusted close-button color/hover contrast while preserving destructive-action styling.
- Refined loading bars to follow rounded UI surfaces and avoid overlapping adjacent actions.
- Improved keyboard-only focus cues rather than showing focus highlights on every mouse interaction.

### Localization and accessibility

- Updated all **18 bundled offline languages**: English, Romanian, German, Spanish, French, Italian, Brazilian Portuguese, Dutch, Polish, Czech, Hungarian, Swedish, Turkish, Russian, Ukrainian, Japanese, Korean and Simplified Chinese.
- Current locale files each contain **1,079 keys**, with zero missing keys relative to English in a structural JSON/key audit.
- Added translation coverage for new Security/Chat interfaces, server creation, players, backups, add-ons, network, diagnostics, system settings, errors and notifications.
- Improved localized confirmation dialogs, accessible labels, error explanations and placeholder/entered-text alignment.
- Added localization audit tooling and workflow definitions. Structural key parity does not guarantee that every translation is idiomatic.

### Privacy, installation and distribution

- Added clearer locally controlled data-management actions, application log cleanup and player-history clearing/retention choices.
- Added controls limiting selected third-party requests and consolidated privacy information around the canonical [Privacy & Responsible Use Notice](https://tuffnode.com/privacy).
- Removed outdated player-image cache disclosures following the removal of remote player-image retrieval.
- Updated installer EULA flow and separate Privacy & Responsible Use acknowledgement.
- Updated `installer/build-installer.ps1` for version-aligned .NET 10 publish, Inno Setup packaging, optional Authenticode signing, SHA-256 checksum and release manifest generation.
- Preserved the Community AppId for intended in-place upgrades from v1.0.1; retained the current user's launch token after elevated installation.
- Added a v1.5.0 release checklist and separate draft for GitHub release notes/community announcement.

### Compatibility and important limits

- Windows x64: support requirements are documented in the project README/installer; Windows 10 Home/Pro compatibility must not be overstated for the .NET 10 target.
- Compatible Minecraft server software is needed for live inventory and TPS; certain data may only be available from a saved playerdata snapshot.
- No Direct Connect, hosted relay, Core-only premium service or Minecraft-server traffic analytics is included with Community.
- Chat history is session-scoped, not a synchronized or persistent messaging service.
- Backup archives remain portable ZIP files; there is no built-in end-to-end backup encryption promise.

For the expanded website-ready presentation, see [v1.5.0 release notes](RELEASE-NOTES-v1.5.0.md). Installer and checksum assets are added when the final validated v1.5.0 package is published.


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
