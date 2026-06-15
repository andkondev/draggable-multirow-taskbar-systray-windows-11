# Draggable, All-in-One Multirow Taskbar & Systray for Windows 11

Drag the top edge of the Windows 11 taskbar to resize it into multiple rows.
Taskbar buttons and ordinary notification-area icons stay in sync with the
chosen row count, giving Windows 11 a more Windows 10-style multirow taskbar
without running several separate taskbar mods at once.

![Three-row taskbar with multirow tray](assets/screenshots/taskbar-3-row.png)

## Features

- Drag the top edge of the taskbar to switch between one or more rows.
- Span taskbar buttons across multiple rows.
- Wrap ordinary notification-area icons across matching rows.
- Keep Wi-Fi, sound, battery, clock, overflow, and the native one-row fallback
  behavior separate from the ordinary tray-icon grid.
- Use conservative first-install defaults: one row, native-looking taskbar
  height, and native single-row tray behavior until you resize.
- Include Windows 10-style running indicators and compact Start/Search/Task View
  hover behavior as part of the integrated setup.
- Use hardcoded integrated defaults; resize by dragging the taskbar edge rather
  than changing Windhawk settings.

## Install

The public Windhawk mod file is:

```text
mods/draggable-multirow-taskbar-systray-windows-11.wh.cpp
```

Until the mod is listed on Windhawk, install it as a local/custom Windhawk mod
from that file. Once it is accepted upstream, this repository should match the
same mod id:

```text
draggable-multirow-taskbar-systray-windows-11
```

## Notes and limitations

- The full Windows Search box can make the Search flyout overlap the taskbar on
  multirow layouts. The Search icon and Search icon-and-label modes behave
  better.
- Hidden tray icons are still controlled by Windows in Settings >
  Personalization > Taskbar > Other system tray icons.
- Disabling and re-enabling the mod can briefly flash while Explorer and
  Windhawk reload taskbar components.

![Full Search box overlap limitation](assets/screenshots/search-box-overlap.png)

## No warranty

This mod is provided as-is, without warranty of any kind. It modifies Windows
Explorer and taskbar behavior through Windhawk hooks, so use it at your own
risk. Windows updates, Windhawk updates, Explorer changes, or taskbar-related
system changes may break behavior.

## Credits and license

This project is licensed under GPL-3.0.

This mod is built on m417z's Windhawk taskbar work:

- Taskbar height and icon size
- Multirow taskbar for Windows 11
- Taskbar tray icon spacing and grid
- Windows 11 Taskbar Styler

Thank you to m417z and the Windhawk project for the original mods and the
platform that makes this kind of taskbar customization possible.

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution details.
