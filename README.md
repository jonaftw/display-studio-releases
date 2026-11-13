# HYPEMAKERZ Display Studio — beta downloads

Factory OS images for the **Orange Pi Zero 2W (4GB)**.

Start at **https://hypemakerz.com/flash2**. Use a spare **64GB microSD card**. Flashing erases the entire selected card.

## 1.0.0-beta.2

Fixes a first-boot permission error in beta 1 that prevented the receiver from starting, leaving the logo visible and the app unable to connect even after joining Wi-Fi. The media filesystem root now belongs to the displaystudio service account. A fresh-filesystem test reproduces beta 1 failure and confirms beta 2 starts, creates its identity and returns HTTP 200 from its health endpoint under that account.

**Use beta 2; beta 1 is superseded.** Reflash a test card.

This is a rebuilt factory image using the saved official Orange Pi Debian 12 system and October 13 Display Studio receiver recovery snapshot. It includes the working hostapd setup hotspot, venue Wi-Fi picker, receiver, kiosk player, and 278 bundled media assets.

- Full 8 GiB disk image, compressed as `.img.xz`.
- Separate system, setup and media partitions. Media storage expands on first boot.
- Saved venue networks, pairing identities, user clips, SSH keys, browser profiles and logs removed. Root filesystem free blocks zeroed.
- New machine identity and receiver token generated on the display.
- SSH password authentication disabled. Optional service access requires your own public key in `HYPESETUP/authorized_keys`.

**Physical boot, phone pairing, venue handoff and playback validation are pending.** This beta is for testing; keep your working card. No boot-time guarantee is made.

## Install

1. Download the `.img.xz` asset and optionally verify its SHA-256 against `DisplayStudio-beta2-SHA256SUMS.txt`.
2. Use balenaEtcher to select that file and your microSD. Flash and wait for validation.
3. Eject, insert into the powered-off screen, then power on.
4. Join **Hypemakerz Screen**, password **Hypemakerz1!**. Open Display Studio, select the screen and set venue Wi-Fi. Pairing passcode: **1942**. Return your phone to the venue network.

If macOS offers to initialize the flashed card, choose Ignore. Its Linux partitions are expected.

## Test checklist

- Cold boot to setup screen; record elapsed time.
- Join hotspot from iPhone and Android.
- Scan venue networks, enter password, reconnect phone and rediscover screen.
- Beam an image and video; confirm playback persists.
- Reboot; confirm saved Wi-Fi and content return.
- Verify available media capacity has expanded beyond the initial 2 GiB.
- Test factory reset and repeat setup.

Third-party software and bundled resources retain their existing licenses; notices are included in the image under `/usr/share/doc` and the receiver library/font license folders. This repository is a release channel, not the mobile app source repository.
