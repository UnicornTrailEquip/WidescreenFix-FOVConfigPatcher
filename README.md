<p align="center">
  <img src="https://i.postimg.cc/zDwH3McS/banner.png" alt="Widescreen Patcher & FOV Calculator — 21:9 / 32:9 Aspect Ratio & INI Config Tool" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-21%3A9%20%26%2032%3A9%20FOV%20Tool-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-widescreen--patch--v1.1-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Widescreen Patcher & FOV Calculator — 21:9 / 32:9 Aspect Ratio & INI Config Tool

**Playing on a 3440×1440 (21:9) or 5120×1440 (32:9) ultrawide monitor and stuck with black sidebars or zoomed-in Vert- FOV? Calculate exact IEEE-754 aspect ratio hex bytes, convert Hor+ FOV angles, and patch local game INI configs safely with automatic backups.**

Widescreen Patcher & FOV Calculator combines three essential ultrawide PC gaming utilities into one offline Windows app: **an IEEE-754 little-endian aspect-ratio hex generator (`39 8E E3 3F` → `8E E3 18 40`), a Hor+/Ver- FOV degree converter, and a safe local `.ini` config patcher with automatic `.bak` backups**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) ultrawide (`21:9` / `32:9`) and multi-monitor PC gamers** configuring single-player titles and engine INI files—not modifying online anti-cheat executables.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Game forces 16:9 black pillarbox bars on 3440×1440 or 5120×1440 | Engine defaults to `16:9` (`1.7778`) resolution or aspect ratio lock | Generate exact `21:9` / `32:9` resolution & aspect ratio values |
| Ultrawide fills the screen, but top/bottom view is zoomed in (`Vert-`) | Game crops vertical FOV instead of expanding horizontal FOV (`Hor+`) | Convert standard `90°` 16:9 FOV into the true `106°` / `121°` Hor+ angle |
| Need IEEE-754 hex bytes for single-player PCGW widescreen fixes | Manually converting float ratios to little-endian hex is error-prone | Auto-detect your monitor resolution and copy exact little-endian hex strings |
| Editing `Engine.ini` or `GameUserSettings.ini` risks breaking config | Manual text edits without backups can corrupt settings | Automatically save `*.ini.bak` before applying any resolution/FOV edit |

## Download for Windows

[**Download WidescreenPatch.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/WidescreenPatch.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `WidescreenPatch.exe`? (Key features)

- Auto-detects your active Windows display resolution (`2560x1080`, `3440x1440`, `3840x1600`, `5120x1440`) and aspect ratio.
- Generates exact IEEE-754 float and little-endian hex strings (`8E E3 18 40`, `39 8E 63 40`, etc.) in 1 click.
- Converts **16:9 Base FOV** to true **Hor+ Ultrawide FOV** (and Unreal Engine `AspectRatioAxisConstraint=AspectRatio_MaintainYFOV`).
- Backs up and patches local game `.ini` configuration files with a 1-click **Restore Original INI** button.

### Sample Output

```text
[WidescreenPatch] Detected Primary Display: 3440x1440 (Ratio: 2.3889 / 21:9)
[INFO] IEEE-754 Hex     : Float = 2.388889 | Little-Endian Hex = 8E E3 18 40
[INFO] Hor+ FOV Math    : 16:9 Base 90°  --->  21:9 Equivalent = 106.3° Hor+
[OK]   UE4/UE5 INI Line : AspectRatioAxisConstraint=AspectRatio_MaintainYFOV
```

The release ZIP is named `WidescreenPatch.zip`; the Windows executable inside is named `WidescreenPatch.exe`.

1. Close Widescreen Patcher before updating or replacing executable files.
2. Click **Download WidescreenPatch.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `WidescreenPatch.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit).

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `WidescreenPatch.exe` runs locally without uploading your files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Fixing zoomed-in `Vert-` cameras in Unreal Engine & Unity games

Adding `AspectRatioAxisConstraint=AspectRatio_MaintainYFOV` to Unreal `Engine.ini` restores proper horizontal ultrawide vision.

### Zero manual hex conversion errors

Copies exact little-endian byte sequences used in PCGamingWiki ultrawide guides.

### Safe `.ini` backups before every change

Preserves `*.ini.bak` so you can revert to stock 16:9 settings anytime.

### Respects anti-cheat boundaries

Focuses on local configuration files and calculators rather than touching protected multiplayer binaries.

## Default folders and configuration paths

Widescreen Patcher stores backups beside any `.ini` config file you edit:

```text
%LOCALAPPDATA%\<GameFolder>\Saved\Config\Windows\
```

Typical directory layout:

```text
Config\Windows\
├── Engine.ini          (Updated with MaintainYFOV / Resolution)
└── Engine.ini.bak      (Automatic backup for 1-click restore)
```

Never patch executables protected by Easy Anti-Cheat, BattlEye, or VAC; stick to single-player titles and official `.ini` config files.

## Quick start guide

Follow these steps to get started:

1. **Extract `WidescreenPatch.zip` and launch `WidescreenPatch.exe`.** Your primary monitor resolution and aspect ratio are detected automatically.
2. **Use the **FOV & Hex Calculator** tab to get your exact `21:9` / `32:9` values.** Copy the Hor+ FOV angle or Unreal Engine `MaintainYFOV` snippet.
3. **Optionally load a local game `.ini` file in the **INI Config Patcher** tab.** Widescreen Patcher creates a `.bak` backup before saving changes.
4. **Launch your game and enjoy full edge-to-edge ultrawide framing.** Click **Restore Original INI** anytime to revert.

### Data safety note

Always keep the generated `*.ini.bak` file if you plan to switch back to a 16:9 monitor or Steam Deck.

## What the status summary shows

Widescreen Patcher displays **detected resolution, exact float ratio, little-endian hex bytes, Hor+ FOV conversion, and INI backup status**.

## FAQ

**What does AspectRatioAxisConstraint=AspectRatio_MaintainYFOV do?**

In Unreal Engine 4 and 5 games, it switches the camera from cropping vertically (`Vert-`) to expanding horizontally (`Hor+`) on 21:9 and 32:9 monitors.

**Is this safe to use with multiplayer games?**

Editing standard `.ini` config files is safe, but never modify `.exe` binaries in games protected by online anti-cheat.

**Does it support 32:9 Super Ultrawide (5120×1440)?**

Yes—it supports 21:9, 32:9, 16:10, and any custom resolution.

## Useful reading

- [PCGamingWiki — Ultrawide & Aspect Ratio Reference](https://www.pcgamingwiki.com/wiki/Glossary:Aspect_ratio)

## More Windows Desktop Utilities

- [MonitorDim-DDCBrightnessControl](../MonitorDim-DDCBrightnessControl) — Hardware DDC/CI external monitor brightness & contrast slider
- [PinTop-WindowAlwaysOnTop](../PinTop-WindowAlwaysOnTop) — Pin any window Always-on-Top & adjust transparency on Windows
- [PadDrift-ControllerPollingTest](../PadDrift-ControllerPollingTest) — Gamepad stick drift & mouse polling rate (1000-8000 Hz) tester
- [Win11-GamingDebloatGuard](../Win11-GamingDebloatGuard) — Windows 11 gaming optimizer & background process cleaner

*Independent open-source desktop utility for Windows.*
