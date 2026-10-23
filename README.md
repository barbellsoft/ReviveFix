# ReviveFix

ReviveFix is a free Windows tool for when a network drive, NAS folder or printer stops working. Click one button: it finds the cause, fixes what is safe to fix, and explains the rest in plain words. You do not need to know what is broken.

Website and full help (11 languages): https://barbellsoft.com/revivefix/

This repository hosts the release builds and their checksums. It is a beta: please report problems (see below).

## Download

Get `ReviveFix.exe` from the [Releases](../../releases) page. Each release lists the SHA-256 checksum of the file.

The program is not code-signed yet, so Windows SmartScreen or your antivirus may show a warning. Before you run it, check the file against the published checksum. In PowerShell:

```powershell
Get-FileHash .\ReviveFix.exe -Algorithm SHA256
```

If the hashes match, choose More info, then Run anyway. ReviveFix starts without administrator rights. Windows asks for them only when a fix needs them, such as starting the print spooler.

## How to use

1. Run `ReviveFix.exe`. Drives already connected to the PC (Z: and so on) and all printers are always checked.
2. If a folder you open by its address does not open, type that address in the box first, for example `\\nas\documents`.
3. Click **Find and fix problems**. ReviveFix fixes what is safe to fix by itself. If a fix needs administrator rights, Windows asks once. If you choose No, nothing changes.
4. Read the results. ✓ works normally. ✔ was broken and ReviveFix fixed it. ⚠ can be fixed after you confirm: click **Fix**. ✗ cannot be fixed from this PC: click **Copy for IT** and send the text to whoever manages the NAS or printer.

## What it can and cannot do

- Reconnects network drives that show a red X in File Explorer.
- Tells you why a folder will not open: the server name cannot be found, the server cannot be reached, the shared folder does not exist, your account has no permission, or the saved password no longer works.
- When a saved password no longer works, removes only that server's saved password so Windows asks you again in its own sign-in window. ReviveFix never asks for or reads passwords.
- Resumes paused printers, turns off "Use printer offline" and starts the print spooler. To clear a stuck print queue it restarts the spooler, but first it lists the waiting jobs that may be lost and asks you.
- Never lowers security settings (it does not turn on SMB1 or guest access, or turn off SMB signing) and never changes settings your company manages. In those cases it explains the problem and gives you the text to send to your IT staff.
- Cannot fix the NAS or printer itself, a server that is turned off, or a paper jam or empty toner. It tells you what to check.
- Sends nothing over the internet.

## Report a problem

Open an issue in this repository. Include your Windows version and the text from the **Copy diagnosis** button. That text contains server, drive and printer names but no passwords. Remove any name you do not want to make public before you post it.

## License

Copyright (c) 2026 Barbellsoft. All rights reserved.

Anyone, including companies and organizations, may use ReviveFix free of charge on any number of computers. You may redistribute the original, unmodified `ReviveFix.exe` free of charge, including on software download sites and on storage media. Don't modify it, wrap it in another installer or download manager, bundle it with other software or offers, or charge for it.

The icon uses Google Material Symbols, licensed under the Apache License 2.0.

## Disclaimer

ReviveFix is provided as is, with no warranty of any kind. You use the program at your own risk. The author is not liable for any damage that results from using it. Restarting the print spooler can delete print jobs that are waiting; ReviveFix asks before it does that.
