# TuffNode Community Changelog

## v0.4.1

This update focuses on safer server lifecycle handling, installed add-on management and Community polish after the v0.4.0 test cycle.

### Server management

- Added a complete server deletion flow.
- Added **Delete** directly to each server row in the Servers page.
- Server deletion remains available from the Manage view.
- Managed servers show a destructive confirmation before permanent deletion.
- Managed-server deletion clearly warns that worlds, plugins/mods, configuration and local server data will be removed.
- Imported servers use a safe **Remove from TuffNode** flow and keep their original Minecraft server folder and files.
- Active servers are stopped before deletion or removal.
- Server lists refresh correctly after deletion/removal.
- Removed the temporary `Delete clicked` debug dialog.

### Add-ons

- Added installed add-on management controls.
- Installed plugins/mods can be enabled, disabled and uninstalled from TuffNode.
- Improved installed add-on state handling.
- Add-on search can be submitted with **Enter**.
- Improved the Community content installation workflow.

### Java and Bedrock cross-play

- Improved Geyser/Bedrock connection information.
- Bedrock UDP addresses are shown alongside the related Java connection addresses for easier discovery.
- Clarified where Bedrock connection information is shown in Network.

### Settings, Sync and Shield

- Moved TuffNode Sync publishing controls into the server settings flow.
- Clarified when server settings apply immediately and when a restart is required.
- Clarified Shield protection refresh behavior and wording.

### Installer and release polish

- Updated the Community application and installer to **v0.4.1**.
- Kept the existing Community installer identity so v0.4.1 upgrades prior Community installations in place.
- Fixed Community desktop shortcut creation.
- Improved installer metadata, documentation and build validation.
- Standardized the installer name as `TuffNode-Community-v0.4.1.exe`.

## v0.4.0

TuffNode Community moves from the initial preview into a much more complete local Minecraft server manager.

### Server management

- Create and import existing Minecraft servers.
- Open or relocate managed server folders.
- Add, change and remove custom server icons.
- Open servers directly from Home and Servers without an extra Manage step.
- Improved server selection and active-server highlighting.

### Runtime and Java

- Configurable minimum and maximum server memory.
- Minimum heap defaults to 512 MB.
- Custom JVM arguments can be changed per server.
- JVM/GC presets are available during server creation.
- Runtime changes are saved immediately and applied on the next server restart.
- Improved Java runtime detection and management.

### Add-ons

- Browse compatible plugins, mods and datapacks.
- Provider support for Modrinth, Hangar and SpigotMC-compatible resources through Spiget.
- Installed add-ons are read directly from the real server folders.
- Local add-on installation from files.
- Installed add-ons can be enabled, disabled and uninstalled from TuffNode.
- Disabled add-ons are kept safely and can be enabled again later.
- Search can be submitted with Enter.

### Java and Bedrock cross-play

- Optional Geyser installation during compatible server creation.
- Geyser can be enabled or disabled later from server management.
- Local and public Bedrock UDP connection addresses are shown only when Geyser is enabled.
- Java connections continue to use the normal server address and port.

### Network and TuffNode Sync

- Improved local and public IP detection with multiple public-IP fallbacks.
- Network page separates normal server connectivity from optional TuffNode Sync publishing.
- TuffNode Sync publishing does not change normal IP, port forwarding, firewall or Java/Bedrock connections.
- Published servers are intended to become visible in a future TuffNode Launcher version.

### Shield

- IP block rules no longer depend only on Windows Firewall.
- Minecraft-level IP blocking is used as a fallback for managed servers.
- Protection status can be refreshed and blocked IP policy reapplied to active servers.

### Backups and files

- Automatic backup scheduling with interval or daily modes.
- Configurable retention.
- Backup location controls and snapshot management.
- Improved Files experience with current location, open-folder and move-location actions.

### Interface

- Major Community UI rebuild with a lighter, server-first layout.
- Reworked Home, Servers, System, Add-ons, Network, Settings and Manage views.
- Expanded server settings and clearer restart/apply behavior.
- Real application version and build metadata in the UI.
- Contact address updated to contact@tuffnode.com.

## v0.2.x / v0.3.x

These versions were internal development milestones between the first public preview and v0.4.0. They were not published as standalone public Community releases.

## v0.1.0-beta

First public Community Preview release.

- Windows desktop application.
- Community Preview installer.
- Desktop and Start Menu shortcuts.
- Application version information.
- License agreement.

This release was an early testing and feedback build.
