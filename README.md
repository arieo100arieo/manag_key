# Manage-Key

Windows installer for **Manage-Key**, an enterprise passkey authenticator. Your
passkeys live in your organization's cloud Hardware Security Module (HSM), not
on the computer.

Download `manage-key-installer.exe` from the latest release.

---

## Installing on your own computer

1. Double-click the installer. **Do not** use "Run as administrator".
2. On the last screen keep **Restart Chrome now** selected and click Finish.
   Chrome closes and reopens — save your work first.
3. Chrome offers the Manage-Key extension. Click **Enable extension**, then pin
   it from the puzzle-piece menu.
4. Open the setup link, JSON file, or QR code your administrator sent you.

Chrome never re-offers an extension you removed before. If it does not appear,
choose **Add manually from the Web Store** on the last screen, or ask your
administrator for the Web Store link.

**Uninstall:** remove Manage-Key from Apps & Features.

---

## Deploying to a fleet (IT)

Install, from an elevated prompt:

```
manage-key-installer.exe /ALLUSERS /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

That installs the native helper to `%ProgramFiles%\Manage-Key` and nothing
else — no window, no Chrome restart, no browser extension.

Add the extension with **one machine-wide Chrome policy**, which covers every
user and every Chrome profile on that machine:

```
HKLM\Software\Policies\Google\Chrome\ExtensionSettings

<extension id> = {"installation_mode":"force_installed","update_url":"https://clients2.google.com/service/update2/crx","toolbar_pin":"force_pinned"}
```

Your Manage-Key administrator provides the extension ID.

Then send each worker a setup link from the admin console (worker → invite →
link + QR). They open it in Chrome and press **Browser extension**.

**Uninstall:** `"C:\Program Files\Manage-Key\unins000.exe" /VERYSILENT`

For the full deployment guide, contact your Manage-Key administrator.

---

Requires 64-bit Windows (x64 or ARM64) and Chrome 120 or newer.

The server, extension, native helper and admin console live in a separate,
private repository. Only the Windows installer is published here.
