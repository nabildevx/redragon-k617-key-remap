# Redragon FIZZ K617 — Key Remap Guide

Custom remap applied to the **Redragon FIZZ K617** 60% mechanical keyboard
(white & grey, software: `Redragon_K617-RGB_Setup.exe`).

Remaps are stored in the keyboard's **onboard memory**, so they work on any
OS (Windows, Linux, BIOS) and persist across reboots. The software is only
needed to apply or change them (Windows only).

---

## Final layout

Right side of the board after the changes:

| Physical key | New function |
|---|---|
| Right Shift | `Up arrow` |
| Right Alt (next to Space) | `FN` (moved here) |
| FN (old position) | `Left arrow` |
| App / Menu key | `Down arrow` |
| Right Ctrl | `Right arrow` |

```
[Right Shift] = ↑
Spacebar | FN | ← | ↓ | →
```

The FN layer is otherwise unchanged: FN+WASD = arrows, FN+Space = color,
FN+Left Alt = color, FN+Win = lock Win key, FN+P = Print Screen, etc. — now
triggered with the FN key in its new position (old Right Alt).

---

## Changes made to `Cfg.ini`

File location (working copy): `Cfg.ini` next to this README.
Installation location: `C:\Program Files (x86)\Redragon K617-RGB\Cfg.ini`

### 1. FN-layer: moved color-change from FN+Right Alt to FN+Left Alt

Section `[FN]`:

| Key | Before | After |
|---|---|---|
| K56 (Left Alt) | *(none)* | `0x09,0x00,0x0b000300` (backlit color) |
| K58 (Right Alt) | `0x09,0x00,0x0b000300` (backlit color) | *(none)* |

### 2. Main layer: arrow cluster

Section `[KEY]` — only the hex triplet was changed; coordinates and trailing
numbers were kept as-is:

| Key | Before | After |
|---|---|---|
| K53 (Right Shift) | `0x02,0xA1` (RShift) | `0x02,0x26` (Up arrow) |
| K58 (Right Alt) | `0x02,0xA5` (RAlt) | `0x02,0xFA` (FN) |
| K59 (FN) | `0x02,0xFA` (FN) | `0x02,0x25` (Left arrow) |
| K60 (App/Menu) | `0x02,0x5D` (App) | `0x02,0x28` (Down arrow) |
| K61 (Right Ctrl) | `0x02,0xA3` (RCtrl) | `0x02,0x27` (Right arrow) |

Note: the new FN key (K58) has **no mapping in the `[FN]` section** — required,
otherwise the board fails to switch to the FN layer.

### 3. FN-layer: added Print Screen on FN+P

Section `[FN]` — new key added (the board has no Print Screen key):

| Key | Mapping |
|---|---|
| K25 (P) | `0x02,0x2C,0x00` (Print Screen) |

---

## How to apply

1. Backup the current file: copy `C:\Program Files (x86)\Redragon K617-RGB\Cfg.ini` somewhere safe.
2. Open the software (or `KeyboardDrv.exe`) and press **Restore** (not Apply).
3. Test: arrow cluster, FN+WASD arrows, FN+Left Alt color, FN+P Print Screen.

## Reset

Hold **FN+ESC** to factory-reset the keyboard, or restore the backup `Cfg.ini`
and press Restore.

## Lost keys (intended tradeoffs)

- Right Alt is gone as a key (it is now FN).
- App/Menu key is gone (now Down arrow).
- Right Shift/Right Ctrl no longer exist (now Up/Right arrows).
