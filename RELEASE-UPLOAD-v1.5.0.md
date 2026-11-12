# Publishing TuffNode Community v1.5.0

**Last stable public release:** v1.0.1 (October 27, 2026).  
**This is a staging checklist, not content for the published GitHub release body.**

1. Merge the prepared documentation branch into public `main` (prefer the release-preparation PR).
2. Build the final installer locally from the latest validated commit in `dutu-dev/TuffNode.Community.dev`, branch `fix/community-managed-servers-window-layout`:
   ```powershell
   .\installer\build-installer.ps1 -Version 1.5.0
   ```
3. Confirm the installer has version v1.5.0 and upgrade testing from v1.0.1 preserved existing servers.
4. In GitHub `dutu-dev/TuffNode-Community`, open **Releases → Draft a new release**.
5. Create tag **v1.5.0** (based on public distribution `main`), title **TuffNode Community v1.5.0**. Use the full body from [GITHUB-RELEASE-v1.5.0.md](GITHUB-RELEASE-v1.5.0.md). Mark the release as **not a prerelease**.
6. Upload the real files from `installer/output/`:
   - `TuffNode-Community-v1.5.0.exe`
   - `TuffNode-Community-v1.5.0.exe.sha256`
   - `checksums.txt`
   - `TuffNode-Community-v1.5.0.release.json`
7. Verify that `Get-FileHash .\installer\output\TuffNode-Community-v1.5.0.exe -Algorithm SHA256` matches the sidecar and release manifest; do not put example or placeholder checksums in the public release.
8. Publish only when the installer and its verification assets have been uploaded. Confirm the installer is downloadable.
9. Refresh website release metadata **after** publication; its changelog is already staged separately and must remain the canonical v1.5.0 change list.

GitHub Actions CI is optional for this release because the maintainer validates the build locally and GitHub Actions minutes are exhausted. Never label an unexecuted CI run as passing.

**Canonical changelog:** [CHANGELOG.md](CHANGELOG.md), mirrored on https://tuffnode.com/changelog.  
**Full notes:** [RELEASE-NOTES-v1.5.0.md](RELEASE-NOTES-v1.5.0.md).
