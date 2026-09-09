# TuffNode Community Changelog

All notable TuffNode Community releases and engineering milestones are listed here, newest first.

> TuffNode moved directly from the original **v0.1.0 beta** line into the Community rebuild that became **v0.4.0**. No public v0.2.x or v0.3.x release was shipped.

---

## v0.6.0-rc.1 — 2026-09-10

**Release Candidate 1** for the v0.6.0 Community release.

This release candidate is the final UI, stability, desktop-integration and power-user polish pass built on top of the modular v0.5.0 architecture.

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
- Release-candidate head: `d5b439d103c65126f5380781fd40115495a2d6f5`

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
| **v0.6.0-rc.1** | 2026-09-10 | Release Candidate |
| **v0.5.0** | 2026-09-08 | Community architecture milestone |
| **v0.4.2** | 2026-09-08 | Stabilization milestone |
| **v0.4.1** | 2026-08-30 | Community release |
| **v0.4.0** | 2026-08-29 | Community rebuild release |
| **v0.1.0-beta** | 2026-08-24 | First public preview |
