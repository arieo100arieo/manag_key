# manag_key

Distribution point for the **cloud-authn** Windows client installer.

## What's here

The installer binary itself is **not committed** to git — it's published as
a release asset. Browse the [latest release](https://github.com/arieo100arieo/manag_key/releases/latest)
to download it.

## Install

1. Download `cloud-authn-installer.exe` from the latest release.
2. Run it. No admin prompt; HKCU + `%LOCALAPPDATA%` only.
3. The installer:
   - drops the native helper (architecture-matched ARM64 / x86_64) to
     `%LOCALAPPDATA%\cloud-authn-native\`
   - drops the Chrome extension (unpacked) to
     `%LOCALAPPDATA%\cloud-authn-extension\`
   - registers the native messaging host under HKCU
   - imports the cloud authenticator's TLS root cert into your user
     trust store via `certutil`
   - opens a local instructions page that walks you through loading
     the unpacked extension into Chrome (3 clicks)
4. Ask your admin for the per-user **onboarding config JSON**. Drop it
   into the extension's onboarding wizard. Done.

## Uninstall

Run "cloud-authn" from **Apps & Features**. Cleans up everything
including the trust-store cert.

## Source

The cloud-authn server, extension, native helper, and admin SPA live
in a separate repository. See `README-DEPLOY.md` in this release for
the build + publish flow.
