# TuffNode Community v0.7.5

TuffNode Community v0.7.5 is the current development line prepared for installer validation. It is not a published GitHub Release yet.

## Current changes

- Integrated the supplied Community application, installer and tray branding assets.
- Added cached catalog icons with provider glyph fallback for add-ons.
- Added clickable add-on detail popups with compatible versions, metadata and exact-version installation.
- Added Windows shell opening for files from the server file browser; folders continue to open inside TuffNode.
- Fixed Appearance accent propagation across the application resource aliases.
- Made the sidebar version, build number and source revision read generated assembly metadata.
- Kept installer versioning, executable metadata, checksums and release manifest on the centralized 0.7.5 source.

## Included reliability work

This development line also includes the documented v0.7.0 and v0.7.1 Community work:

- Runtime and JVM policy improvements.
- Network reachability and diagnostics.
- Hardened add-on downloads, validation and rollback.
- Configuration, lifecycle and backup safety.
- Single-instance and telemetry performance improvements.
- Installer preflight and release-integrity checks.

## Installer output

The release build is expected to produce:

- TuffNode-Community-v0.7.5.exe
- TuffNode-Community-v0.7.5.exe.sha256
- checksums.txt
- TuffNode-Community-v0.7.5.release.json

The public v0.6.0 installer remains the current downloadable release until v0.7.5 is built, validated and attached to GitHub Releases.

## Product boundary

This release remains TuffNode Community. It does not include Core-only Always-On Service, remote management, player tunneling, remote files, Blackbox, Predictive Failure, Surgical Restore or Player Time Machine.

Support: contact@tuffnode.com

https://tuffnode.com
