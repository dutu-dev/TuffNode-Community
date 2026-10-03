# TuffNode Community v0.7.6

## Release status

v0.7.6 is the current Community release. Release metadata is published; the signed Windows installer asset is attached separately when the final binary is uploaded.

## Highlights since v0.6.0

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

## Validation

- Release branch: work/audit-and-improvements.
- Inno Setup entry point: installer/TuffNodeSetup.iss.
- Build command: pwsh ./installer/build-installer.ps1 -Version 0.7.6.
