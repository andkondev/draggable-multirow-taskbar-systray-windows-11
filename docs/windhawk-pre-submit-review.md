# Windhawk Pre-Submit Review

This repository is the public staging repo for the Windhawk mod:

`draggable-multirow-taskbar-systray-windows-11`

Windhawk upstream submission should be a pull request to
`ramensoftware/windhawk-mods` containing only this file:

`mods/draggable-multirow-taskbar-systray-windows-11.wh.cpp`

## Current Release File

- Mod file: `mods/draggable-multirow-taskbar-systray-windows-11.wh.cpp`
- Expected Windhawk id: `draggable-multirow-taskbar-systray-windows-11`
- Version: `0.1.0`
- Author: `andkon`
- GitHub: `https://github.com/andkondev`
- Homepage: `https://andkon.dev/`
- License: `GPL-3.0`
- SHA-256: `D6AD7C3B9BDA6F13463A9A6352ACB24972902AAD8788D3A4E04E6F06AB98D712`

## Public Assets

The Windhawk Details markdown uses GitHub raw image URLs. Verify both load
before opening the upstream Windhawk PR:

- `https://raw.githubusercontent.com/andkondev/draggable-multirow-taskbar-systray-windows-11/main/assets/screenshots/taskbar-3-row.png`
- `https://raw.githubusercontent.com/andkondev/draggable-multirow-taskbar-systray-windows-11/main/assets/screenshots/search-box-overlap.png`

## Known Limitations To Review

- The full Windows Search box can make the Search flyout overlap the taskbar on
  multirow layouts. Search icon and Search icon-and-label modes behave better.
- Hidden tray icons are still controlled by Windows settings, not this mod.
- Disabling and re-enabling the mod can briefly flash while Explorer and
  Windhawk reload taskbar components.
- The mod intentionally exposes no Windhawk settings; resizing is done by
  dragging the taskbar edge.

## Attribution To Review

This mod is built on m417z's Windhawk taskbar work:

- Taskbar height and icon size
- Multirow taskbar for Windows 11
- Taskbar tray icon spacing and grid
- Windows 11 Taskbar Styler

Review `THIRD_PARTY_NOTICES.md` before submitting upstream.

## Suggested Windhawk PR

Title:

`Add draggable multirow taskbar and systray mod for Windows 11`

Body:

```markdown
Adds a Windows 11 taskbar mod that combines draggable multirow taskbar sizing,
multirow taskbar buttons, ordinary notification-area icon wrapping, and
Windows 10-style taskbar indicators into one integrated Windhawk mod.

The mod starts conservatively at one native-height row and exposes no Windhawk
settings. Users resize by dragging the top edge of the taskbar. Ordinary tray
icons wrap across rows when the taskbar is resized, while Wi-Fi, sound, battery,
clock, overflow, and native one-row fallback behavior remain separate.

Known limitations are documented in the mod details/readme, including the full
Windows Search box flyout overlap on multirow taskbars.
```
