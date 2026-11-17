# 🎞 Bad Movies Overlay

**Play video clips on top of everything else on your screen, with the background colour keyed out to transparent.**

Load clips into a board (like a soundboard, but for video), pick the colour to remove for each one, choose where it sits on the screen, and trigger it with a click or a global hotkey. The clip floats over whatever else is running, even a movie playing in VLC, so you can put info, reactions or graphics on screen without touching the movie underneath.

Made by David for [BadMovies.co](https://badmovies.co), a community that watches bad movies together in VR four times a week.

**[⬇ Download the latest installer](../../releases/latest)** · Windows 10/11 (64-bit) · free

---

## Features

### The board
- Tiles for every clip, with a thumbnail, name, colour, hotkey and a 🔑 badge when keying is on
- Categories (tabs): create, rename (double-click), drag a clip onto a tab to move it
- Drag tiles to reorder, resize tiles with the Size slider
- Drag video files straight onto the window to add them, or use **＋ Add clips**
- **📋 Add from link**: copy a YouTube (or other video site) link, click the button, and the video is downloaded (up to 1080p MP4) straight into the board. The downloader (yt-dlp) is fetched on first use and keeps itself updated. Please only download videos you have the right to use
- Click a tile to show the clip, click again to stop. **Stop all** button and a global hotkey (default `Ctrl+Alt+Backspace`)
- Per-clip global hotkeys that work while another app has focus

### Chroma key (per clip, remembered)
- **Click the colour you want gone**: pause the preview on any frame and click the background. The preview shows a checkerboard where it is now transparent
- **Auto-detect** guesses the background colour from the four corners of the frame
- **Tolerance**, **Edge softness** and **Spill clean-up** sliders, plus **Show original** to compare
- Keying runs on the GPU (WebGL) so it stays smooth, and is the same in the preview and on screen
- Key colour, settings and the frame you picked from are saved with the clip

### On-screen overlay
- Each playing clip gets its own transparent, always-on-top window. It is **click-through** and never steals focus, so the app underneath keeps working
- Sits above borderless-fullscreen players (VLC's normal fullscreen, browsers, most games in borderless mode). Programs in *exclusive* fullscreen cannot be covered by any overlay
- **Position and size, per clip**: pick the display, type X / Y / W / H, snap to a corner or the centre, or use size presets (15 / 25 / 33 / 50 % of the screen)
- **Tile pictures**: in the editor, pause on the frame you like and press **📷 Use this frame as the tile picture**; tick *Cut out the key colour* to show just the subject instead of a green rectangle
- **Position on screen map**: the editor shows your whole display with the clip on it, exactly as it will look. Drag it, resize from the corners, or hit **⛶ Fullscreen** / **◱ Fit screen**. If the clip is playing it moves live, handy mid-stream
- **Move & resize on screen**: drag the real overlay where you want it, resize from the corners (proportions stay locked unless you turn that off)
- **⛶ Fill screen**: one click to cover the whole display, including the area under the taskbar
- Works across multiple monitors; each clip remembers its display
- Per-clip **opacity**, **volume**, **mute** and **loop until stopped**

### Video optimizer
- **⚡ Optimize this clip**, **⚡ Optimize all**, or let it happen automatically when clips are added (on by default, switch off in 📁 Library)
- Re-encodes to the format the app plays best: H.264 video (near-lossless quality) and AAC audio in an MP4, constant frame rate, capped at 1920 px wide. Usually much smaller than the original and fixes files that misbehave (odd sizes, variable frame rate, HEVC / MKV that the player can't decode)
- Clips that can't be played as-is are converted automatically when added
- The original is only deleted once the new file has been checked and plays

### Edit in FilmCraft
- If you have **FilmCraft** installed, the clip settings show **✂ Edit in FilmCraft**. It opens the clip in FilmCraft so you can trim or edit it, then **Finish — bring it back** exports it, re-encodes it with the optimizer and swaps it into your board with all its settings intact
- Hidden automatically when FilmCraft isn't installed

### Your library
- Everything lives in one visible, portable folder: `Documents\Bad Movies Overlay` (clips, thumbnails, `library.json`, and automatic daily backups, keeping the last 14)
- **Move library…** relocates it to another drive; it copies, verifies every file, and only then removes the old copy
- **Clean unused files** removes clips no longer on the board
- The main window remembers its position, size and monitor between launches
- Updates and uninstalls never touch your library

### Updates
- The installed app checks GitHub for new versions on launch and every 4 hours. When one is ready a green **Update vX — Restart** button appears in the top bar. (It checks about 5 seconds after launch, so if you opened the app just before a release, relaunch and wait ~20 seconds.)

---

## Install

1. Download `BadMoviesOverlay-Setup-x.y.z.exe` from the [latest release](../../releases/latest) and run it.
2. Windows SmartScreen will warn that the publisher is unknown, because the app is not code-signed. Click **More info → Run anyway**.
3. It installs per-user (no admin needed) and creates a Start menu entry.

**Requirements:** Windows 10 or 11, 64-bit. FilmCraft is optional. No other software is needed; the video tools are bundled.

## Quick start

1. **＋ Add clips** (or drag video files in, or copy a YouTube link and press **📋 Add from link**). MP4 (H.264), WebM and MOV are best; anything else is converted for you.
2. Click a tile's **⚙**. Pause on a frame and **click the background colour** in the preview. Adjust Tolerance and Edge softness until the checkerboard looks right.
3. Under **Where on screen**, choose the display and size, or hit **🖱 Move & resize on screen** and drag the real overlay into place. Press **Done** (or Enter) when happy.
4. **Save**. Click the tile, or press its hotkey, to put the clip on screen. Click again to stop it. `Ctrl+Alt+Backspace` stops everything.

Tip: shoot or find clips on a solid, evenly-lit background (green or blue screen is ideal, but any flat colour that isn't in the subject works).

## Supported files

| Type | Notes |
|---|---|
| MP4 / M4V / MOV | Best choice (H.264). Other codecs are converted automatically |
| WebM | Plays natively |
| MKV / OGV | Converted to MP4 on add |

Audio is kept (use **Mute** per clip if you only want the picture).

## Where things are stored

| What | Where |
|---|---|
| Library (clips, thumbnails, `library.json`, backups) | `Documents\Bad Movies Overlay` (movable) |
| App settings, window position, log | `%APPDATA%\Bad Movies Overlay` (`config.json`, `overlay.log`) |

## Troubleshooting

- **The overlay doesn't show over a game or player.** It can't cover *exclusive* fullscreen. Switch the program to borderless / windowed-fullscreen.
- **A clip won't play or the editing window closes.** Click **⚡ Optimize this clip**; the file is probably in a codec the player can't decode.
- **Keyed edges look soft.** Raise **Edge softness** a little, or lower **Tolerance**. Optimized clips use standard 4:2:0 colour, which softens very fine edges slightly.
- **A gap at the bottom where the taskbar is.** Fixed in v0.5.1. If it ever returns, send the file `%APPDATA%\Bad Movies Overlay\overlay.log` with the report; it records the size requested against the size Windows gave.
- **The update button didn't appear.** Close and reopen the app and wait about 20 seconds. You can always install the newest setup file over the old one; your library is kept.
- **A hotkey is "unavailable".** Another program already owns that key combination. Pick a different one in the clip's settings.
- **The taskbar icon looks old after updating.** Unpin and re-pin the shortcut; Windows caches icons.

## Release history

| Version | Highlights |
|---|---|
| **0.8.1** | 📷 **Choose the tile picture**: pick any frame (optionally with the key colour cut out) so clips are easy to tell apart on the board |
| **0.8.0** | 🖥 **Position on screen** map in the editor (drag/resize live), **Fullscreen** and **Fit screen** buttons, simpler Where-on-screen panel |
| **0.7.0** | 📋 **Add from link**: grab a video from a copied YouTube link straight into the board |
| **0.6.0** | ✂ **Edit in FilmCraft**: open a clip in FilmCraft, trim/edit, and bring it back re-encoded |
| **0.5.1** | Fixed the gap at the bottom of the screen when a full-screen clip starts playing; adds `overlay.log` diagnostics |
| **0.5.0** | ⚡ **Video optimizer** (H.264/AAC, smaller files), automatic conversion of unplayable clips; an undecodable video no longer closes the editing window |
| **0.4.2** | More stable **Fill screen** (verifies and retries the window size, picks the right monitor) |
| **0.4.1** | Main window remembers its position, size and monitor |
| **0.4.0** | ⛶ **Fill screen** button in Move & resize |
| **0.3.0** | Per-clip **Mute** |
| **0.2.1** | New bright-green app icon |
| **0.2.0** | Installer and automatic updates |
| **0.1.0** | First version: board, per-clip chroma key, on-screen overlay, position and size, library (not published as a download) |

Every version is listed under [Releases](../../releases) with its installer.

## About

Bad Movies Overlay is a companion to the Bad Movies Soundboard and is built with Electron. The source code is private; this repository only hosts the installers and release notes.

Questions, bugs or ideas? Tell David on the BadMovies.co community.
