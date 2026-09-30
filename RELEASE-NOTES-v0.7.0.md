# TuffNode Community v0.7.0

TuffNode Community v0.7.0 is the next Community release focused on lightweight runtime management, safer networking diagnostics, hardened add-on handling, lifecycle correctness and release integrity.

> Status: release preparation. v0.6.0 remains the current public download until the v0.7.0 installer is built, validated and attached to the GitHub Release.

## Highlights

### Runtime and JVM

- Managed Auto, G1GC, ZGC and Shenandoah garbage-collector profiles.
- Centralized JVM launch policy for heap, GC and additional arguments.
- Low-frequency centralized CPU/RAM sampling.
- Startup-only Java child discovery for batch-script servers.

### Network diagnostics

- Public TCP reachability checks with listener, firewall and NAT/CGNAT-oriented explanations.
- Cached and deduplicated external probes.
- Stale probe results are ignored after restarts, runtime identity changes or effective-port changes.
- External server.properties port changes remain synchronized with TuffNode.

### Add-ons hardening

- HTTPS-only trusted provider downloads with redirect validation.
- Bounded download/import sizes and empty-payload rejection.
- Plugin/mod JAR validation and datapack ZIP + root pack.mcmeta validation.
- Validated local datapack import.
- Rollback-safe tracked add-on updates with source metadata and SHA-256.
- Concrete Spigot/Spiget version tracking.
- Persistent restart-required state while the server is active.

### Lifecycle, configuration and backups

- Unsaved configuration is protected when leaving or switching the active server workspace.
- Server relocation coordinates with runtime filesystem ownership and restores metadata on rollback.
- Config paths reject junction/symlink escapes.
- Visual/raw configuration saves are rollback-consistent.
- Backup create, restore and delete operations are serialized and path-confined.
- Restore validates capacity and cleans rollback staging safely.
- UI/runtime observers are disposed cleanly during shutdown and ownership changes.

### Desktop reliability

- Single-instance desktop guard prevents duplicate app/tray instances.
- Hidden metrics pages suspend updates.
- Telemetry-only runtime changes avoid unnecessary UI refresh and player/backup churn.

## Installer and release assets

The v0.7.0 release build is expected to produce:

- `TuffNode-Community-v0.7.0.exe`
- `TuffNode-Community-v0.7.0.exe.sha256`
- `checksums.txt`
- `TuffNode-Community-v0.7.0.release.json`

The installer build performs a release preflight and verifies centralized versioning, publisher identity, application metadata, installer text, SHA-256 and release-manifest integrity.

Recommended GitHub Release settings once final validation passes:

- **Tag:** `v0.7.0`
- **Release title:** `TuffNode Community v0.7.0`
- **Target:** `main`
- **Pre-release:** No
- **Latest:** Yes

## Product boundary

This release remains TuffNode Community. It does not include Core-only Always-On Service, remote management, player tunneling, remote files, Blackbox, Predictive Failure, Surgical Restore or Player Time Machine.

## Upgrade note

The existing Community AppId is preserved so prior Community installations upgrade in place. Keep normal backups of important Minecraft worlds and configuration before major upgrades.

## Feedback

contact@tuffnode.com

https://tuffnode.com
