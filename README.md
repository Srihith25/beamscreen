# BeamScreen

Use your TV as a wireless second screen for your Mac or Windows PC, mirrored or extended, with sound, over your home network. No cables, no dongles.

- **Extend:** the TV becomes a real second display. Drag windows onto it.
- **Mirror:** show your computer's screen on the TV.
- **Sound where you want it:** play your computer's audio through the TV, or keep it on the computer.
- **Low latency:** hardware encoding and decoding with no buffering. Typically under 100 ms on a good network.
- **Works with almost any TV:**
  - Google TV and Android TV, through the BeamScreen TV app;
  - other smart TVs (Samsung, LG, Fire TV…), phones, tablets and laptops, through their **web browser**. Nothing to install on them.
- **Private by design:** a TV or browser only receives your screen after you pair it with a code shown on its own screen.

## Download

Get the latest version from the [**Releases**](https://github.com/Srihith25/beamscreen/releases) page:

| File | For |
|---|---|
| `BeamScreen-<version>-macOS.zip` | Mac: macOS 14.2 or later, Apple silicon or Intel |
| `BeamScreen-<version>-Windows-x64.zip` / `-arm64.zip` | Windows 10 (2004) or later; GPU with hardware H.264 encoding |
| `BeamScreen-<version>-release.apk` | Google TV / Android TV, Android 7.0 or later |
| `SHA256SUMS.txt` | Checksums to verify your download |

**Check your download.** In Terminal (Mac), in the download folder:
`shasum -a 256 -c SHA256SUMS.txt --ignore-missing`. On Windows (PowerShell):
`Get-FileHash .\BeamScreen-<version>-Windows-x64.zip`, then compare with the value in `SHA256SUMS.txt`.

## Install

### Mac

1. Unzip and move **BeamScreen** to Applications.
2. The app isn't notarized by Apple yet, so macOS blocks it the first time. Open it once, and when macOS says it can't verify the developer, click **Done**. Then open **System Settings → Privacy & Security**, scroll to the message about BeamScreen and click **Open Anyway**. You only do this once per version.
   Don't turn off Gatekeeper or use `xattr` to skip this.
3. Allow **Screen Recording**, so BeamScreen can show your screen on the TV. If you want the sound on the TV, also allow **System Audio Recording**. Only BeamScreen needs these permissions; never give them to other apps for it.

### Windows

1. Unzip anywhere and run `BeamScreen.exe`. No installer needed.
2. The app isn't code-signed yet. If SmartScreen says "Windows protected your PC", click **More info → Run anyway**.
3. If Windows Firewall asks, allow BeamScreen on **private networks** only.

### Google TV / Android TV

The TV app isn't in the Play Store yet, so you install it once from your computer:

1. On the TV: **Settings → System → About**, then select **Android TV OS build** 7 times to turn on developer options.
2. **Settings → System → Developer options:** turn on **Network debugging** (or USB debugging), and note the TV's IP address.
3. On your computer, install Android's `adb` tool, then run:
   `adb connect <tv-ip>:5555` and `adb install BeamScreen-<version>-release.apk`.
   Accept the prompt on the TV.
4. Open **BeamScreen** on the TV once. Then turn **Network debugging** off again.

### Other smart TVs, phones and laptops (Mac only for now)

Nothing to install. In BeamScreen on the Mac, turn on **"Allow TVs to connect from their web browser"**. Then open the address it shows (like `http://192.168.1.20`) in the TV's web browser.

## Use

1. Open BeamScreen and pick your TV. Browser TVs show up as "(web browser)".
2. Choose **Mirror** or **Extend**, a resolution, and where the sound goes. Click **Connect**.
3. **The first time with each TV,** it shows a 6-digit code. Type it on your computer to pair. After that, it connects without a code.

To stop, click **Disconnect**, quit the app, or press **Back** on the TV remote.

## Safety and privacy

- A TV app or browser only gets your screen after you **pair** it with the code on its own screen. Paired devices prove themselves on every connection, so other devices on your network can't take over your TV or receive your screen.
- The browser option is **off at every launch** and turns itself off after 30 minutes without a stream. It only answers devices on your local network.
- You can remove pairings at any time: **Forget Paired TVs / TV Browsers** on the computer, **Forget paired computers** on the TV.
- BeamScreen has no accounts, no cloud and no analytics. Everything stays on your local network.
- The video stream itself isn't encrypted. Use BeamScreen only on a network you trust (your home), not on public Wi-Fi.

Found a security problem? Please report it privately through this repository's **Security → Report a vulnerability**, not in a public issue.

## Known limitations

- Windows: Extend needs a separately installed virtual display driver, and Windows can't send to TV browsers yet.
- Extend on the Mac uses a macOS feature that Apple doesn't document; a future macOS could change it.
- One computer per TV at a time.

## License

Copyright © 2026 Srihith Dhulipala. All rights reserved.

BeamScreen is free to download and use under the [BeamScreen License](LICENSE). The source code isn't public, and you may not copy, modify, redistribute or sell the apps.
