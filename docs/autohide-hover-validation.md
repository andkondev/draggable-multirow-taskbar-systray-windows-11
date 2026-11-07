# Auto-hide hover-reveal fix

This change addresses [issue #1](https://github.com/andkondev/draggable-multirow-taskbar-systray-windows-11/issues/1): the resize grip overlaps Windows' bottom-edge
reveal strip when the primary taskbar is auto-hidden. The original build failed
to reveal on the primary display while the secondary display worked.

`EdgeResizeTaskbarHasUsableGrip` intersects the taskbar window with its monitor
and compares the visible height with the DPI-scaled grip height. Both input hit
tests decline the reveal strip, and the separate grip window is hidden there.
Normal dragging resumes when the taskbar is visible. The change does not write
the Windows auto-hide state, retain a separate preference, or enforce a startup
timer.

## Physical-device verification — November 6, 2026

Windows 11 build 26300.9711 with Windhawk 1.7.3:

- Primary: laptop panel, 1920×1080, 125% scaling.
- Secondary: external display, 3840×2160, 300% scaling, extended to the right.
- Bottom taskbars; two and three rows.
- Tested source SHA-256:
  `62DE8A75DC25FC6F41188A68B840CAFEA0EB803C2598DC0F08FC079CCFDEEB75`.

The original primary/secondary asymmetry was reproduced before installing the
candidate. With the candidate, both monitors passed hide → bottom-edge hover →
reveal → hide at two and three rows. Actual mouse dragging changed the primary
height from 120 to 180 physical pixels and back; the secondary height followed
from 288 to 432 pixels and back. Taskbar and ordinary tray row settings stayed
in sync. Dragging passed with auto-hide enabled and disabled.

The actual Windows Settings auto-hide checkbox was switched on/off immediately
after loading the candidate. Both choices were respected. After an orderly
Explorer exit and restart with auto-hide on, the setting remained on through
the first-minute observation and hover reveal worked on both monitors.

## Restart test interpretation

Forced process termination is distinct from an orderly Explorer exit. Initial
tests force-killed Explorer shortly after changing auto-hide. The on state was
lost even with the mod disabled: the live appbar state had changed, but the
saved taskbar flags had not. The same distinction was observed through the
Settings UI. These failed forced-termination checks are retained in the local
evidence; they are not evidence that this patch forces auto-hide off.

The orderly restart sends Explorer its exit request and waits for process exit
before starting it again. The saved flags changed on exit, and the on preference
survived restart. This test technique is also used by
[ExplorerPatcher's ExitExplorer implementation](https://github.com/valinet/ExplorerPatcher/blob/master/ExplorerPatcher/utility.h).

## Coverage boundaries

Build changes were performed with the shell stopped. This does not resolve or
validate the live DLL unloading crashes observed while testing PR #2. Natural
reboot/logon, swapping the primary display, vertically stacked displays and
top/side taskbars were not tested.

The Settings window was not reliably available after an orderly shell exit.
An additional UI off-state recheck was blocked; earlier checkbox on/off checks
completed successfully. The final off-state persistence check passed using the
native appbar API followed by orderly exit, with 26 samples over approximately
52 seconds after restart. It is recorded separately from the checkbox tests.

The whole session recorded no Explorer Application Error/WER crash events.
The original DLL/source hashes, row settings, live appbar state, exact saved
taskbar registry data and original duplicate-display configuration were verified
after restoration. All test tasks/workers and the installed candidate DLL were
removed. The fixed source is retained separately from the restored laptop build.

The first display-setup attempt aborted because the harness cached the original
one-screen .NET monitor list after extending the desktop. The harness was fixed
to enumerate current monitors through Windows before the successful two-screen
test. Screenshots and JSON measurements are retained locally with active DLL,
screen coordinates, DPI, taskbar geometry, row settings and cursor positions.
