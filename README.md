# Manage-Key

Distribution point for the **Manage-Key** Windows client installer.

## Install

1. Download `manage-key-installer.exe` from the latest release.
2. Run it. No admin prompt; HKCU + `%LOCALAPPDATA%` only.
3. Restart Chrome. The Manage-Key extension installs itself from the
   Chrome Web Store.
4. Ask your admin for the per-user **onboarding config JSON**. Drop it
   into the extension's onboarding wizard. Done.

## Uninstall

Remove **Manage-Key** from **Apps & Features**. Chrome drops the
extension on its next launch.

## Source

The Manage-Key server, extension, native helper, and admin SPA live
in a separate (private) repository.
