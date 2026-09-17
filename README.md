# SPO - Hardened Sandboxie-Plus Box

Hardened Sandboxie-Plus configuration for safer browsing and testing unknown files. Red box, auto-clear on close.

> Built on [Sandboxie-Plus](https://github.com/sandboxie-plus/Sandboxie) by David Xanatos (open source). This repo contains only my original hardening config, not Sandboxie itself.

## What it does

- Blocks sandboxed apps from reading Documents, Desktop and data drives (privacy mode)
- Blocks writes from escaping to the real system (everything stays in the sandbox)
- Drops admin rights, closes spooler, disables clipboard from sandbox
- Blocks network shares, disables recovery prompts
- Auto-deletes box contents when the last sandboxed program closes
- Windows Defender still scans inside the sandbox

## Files

- `SPO-Config.ini` - the `[SPO]` box snippet for `C:\Windows\Sandboxie.ini`
- `SPO-Client-EN.txt` - end-user guide (English)
- `LICENSE-SPO.txt` - config license and credit

## Install (Windows + Sandboxie-Plus required)

1. Install Sandboxie-Plus.
2. Open SandMan > Options > Edit Configuration (admin approval needed).
3. Paste the contents of `SPO-Config.ini` at the end, save, then Options > Reload Configuration.
4. A red `SPO` box appears.

Or create it in the UI: Sandbox > Create New Box > name `SPO` > type Data Protection (blue), then enable Drop Admin Rights + AutoDelete.

## Use

1. Right-click browser > Run Sandboxed > SPO (check red border).
2. Right-click any file > Run Sandboxed > SPO.
3. When done: SandMan > SPO > Terminate All Programs (clears the box).

## Verified (2026-09-17, Sandboxie-Plus v1.17.9)

- Write containment: file written from inside to Desktop never reached real Desktop, found only under `C:\Sandbox\...\SPO\...`
- Read block: private desktop file unreadable from inside SPO
- EICAR 68-byte standard AV test: downloaded inside SPO via sandboxed curl, stayed in sandbox, detected by Defender as `Virus:DOS/EICAR_Test_File`

## Limits

App sandbox, not a full VM. It shares the Windows kernel. For suspected kernel-level malware use a full VM. Keep Defender on and Sandboxie-Plus updated.

## Credit

SPO config (c) 2026 Sohan. Share/modify allowed with credit. Donate (Binance UID): 1223548662. Details in `LICENSE-SPO.txt`.
