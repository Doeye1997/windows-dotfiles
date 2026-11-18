# komorebi layouts and hotkeys

Recorded 2026-11-17 from the live setup on this machine.

## Layouts

The YASB layout menu lists 9 entries. These are komorebi's predefined layouts,
the `DefaultLayout` enum in `komorebi-layouts/src/default_layout.rs`
(repo `LGUG2Z/komorebi`, branch `master`). They are layout strategies, not
separate algorithms and not Windows disk partitions.

Source diagrams (ASCII, from the enum doc comments):

```text
BSP                      Columns              Rows
+-------+-----+          +--+--+--+--+        +-----------+
|       |     |          |  |  |  |  |        |-----------|
|       +--+--+          |  |  |  |  |        |-----------|
|       |  |--|          |  |  |  |  |        |-----------|
+-------+--+--+          +--+--+--+--+        +-----------+

VerticalStack            HorizontalStack
+-------+-----+          +------+------+
|       |     |          |             |
|       +-----+          |------+------+
|       |     |          |      |      |
+-------+-----+          +------+------+

UltrawideVerticalStack              RightMainVerticalStack
+-----+-----------+-----+           +-----+-------+
|     |           |     |           |     |       |
|     |           +-----+           +-----+       |
|     |           |     |           |     |       |
|     |           +-----+           +-----+-------+
|     |           |     |
+-----+-----------+-----+

Grid (shape depends on window count)
+-----+-----+   +---+---+---+   +---+---+---+
|     |     |   |   |   |   |   |   |   |   |
|     |     |   |   |   |   |   |   |   |   |
+-----+-----+   |   +---+---+   +---+---+---+
|     |     |   |   |   |   |   |   |   |   |
|     |     |   |   |   |   |   |   |   |   |
+-----+-----+   +---+---+---+   +---+---+---+
  4 windows       5 windows       6 windows

Scrolling
+--+--+--+--+--+--+
|     |     |     |
|     |     |     |
|     |     |     |
+--+--+--+--+--+--+
```

The enum comment says: "If any new layout is added, please make sure to
register the same in `DefaultLayout::cycle`." These 9 are the complete
cycleable set.

Split ratios come from `LayoutOptions.column_ratios` and `row_ratios`
(up to 5 values, each clamped to 0.1..0.9, truncated once the sum reaches 1.0).

The menu entries below the divider are state toggles, not layouts:
Toggle Tiling, Toggle Monocle, Toggle Pause.

## Hotkeys

From `C:\Users\Administrator\.config\whkdrc` (shell: powershell). Not pressed to
verify; read from the file only.

### Focus
- `alt + h/j/k/l` : focus left/down/up/right
- `alt + shift + [` / `]` : cycle focus previous/next

### Move
- `alt + shift + h/j/k/l` : move window left/down/up/right
- `alt + shift + enter` : promote focused window

### Stack
- `alt + arrow` : stack in that direction
- `alt + ;` : unstack
- `alt + [` / `]` : cycle stack previous/next

### Resize
- `alt + =` / `alt + -` : resize horizontal increase/decrease
- `alt + shift + =` / `alt + shift + -` : resize vertical increase/decrease

### Window state
- `alt + q` : close
- `alt + m` : minimize
- `alt + t` : toggle float
- `alt + shift + f` : toggle monocle
- `alt + p` : toggle pause
- `alt + shift + r` : retile

### Layout
- `alt + x` : flip layout horizontal
- `alt + y` : flip layout vertical
- No direct hotkey selects a specific layout. The menu is mouse-only;
  middle/right click cycles the list.

### Workspaces
- `alt + 1..9` : focus workspace 0..8 (INET .. MISC)
- `alt + shift + 1..9` : move window to workspace 0..8
- `alt + ,` / `alt + .` : cycle workspace previous/next
- `alt + shift + ,` / `alt + shift + .` : move window to previous/next workspace

### Manager
- `alt + o` : restart komorebi (whkd, bar, masir)
- `alt + shift + o` : reload configuration
- `alt + i` : toggle shortcut overlay

### Key names
`oem_4` = `[`, `oem_6` = `]`, `oem_1` = `;`, `oem_plus` = `=`,
`oem_minus` = `-`, `oem_comma` = `,`, `oem_period` = `.`.

## Autostart

Set 2026-11-18. komorebi starts at logon through the per-user Run key:

```text
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
  komorebi = "C:\Program Files\komorebi\bin\komorebic.exe" start --whkd
```

Verified by `reg query` readback. Not verified by an actual reboot.

GlazeWM autostart: none found, so nothing was removed. Checked HKCU and HKLM
`Run`, `StartupApproved\Run`, `StartupApproved\StartupFolder`, both Startup
folders, and scheduled tasks. The GlazeWM config `startup_commands` only
launches YASB; it is not a GlazeWM autostart switch. `GlazeWM.lnk` sits in
the Start Menu Programs folder, not Startup.
