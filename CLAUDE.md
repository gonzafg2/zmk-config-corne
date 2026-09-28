# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a ZMK firmware configuration repository for a Corne (crkbd) split mechanical keyboard using nice!nano v2 controllers. ZMK (Zephyr Mechanical Keyboard) is an open-source keyboard firmware built on the Zephyr RTOS. ZMK is pinned to `main` in `config/west.yml` (Zephyr 4.1, board `nice_nano//zmk`). The host is macOS with the **Latin American** layout on an **ISO** keyboard type.

## Key Commands

### Building Firmware
- **GitHub Actions**: Push changes to trigger automatic builds via `.github/workflows/build.yml` (matrix in `build.yaml`)
- **Local builds**: Requires ZMK toolchain setup (west, Zephyr SDK)
  ```bash
  west build -d build/left -b nice_nano//zmk -S studio-rpc-usb-uart -- \
    -DSHIELD=corne_left -DCONFIG_ZMK_STUDIO=y -DZMK_CONFIG="/absolute/path/to/zmk-config-corne/config"
  west build -d build/right -b nice_nano//zmk -- \
    -DSHIELD=corne_right -DZMK_CONFIG="/absolute/path/to/zmk-config-corne/config"
  ```

### Firmware Files
After successful GitHub Actions build, download the `firmware` artifact:
- Flash `corne_left-nice_nano__zmk-zmk.uf2` to the left half (central, includes ZMK Studio)
- Flash `corne_right-nice_nano__zmk-zmk.uf2` to the right half
- Flash `settings_reset-nice_nano__zmk-zmk.uf2` to both halves to reset settings (Bluetooth must be re-paired afterwards)
- Keymap-only changes only need the left (central) half

## Architecture & Structure

### Configuration Files
- **build.yaml**: Build matrix. Central-only settings go in `corne_left`'s `cmake-args` (the shared `corne.conf` applies to both halves and makes `corne_left.conf` be ignored): the `studio-rpc-usb-uart` snippet, `CONFIG_ZMK_STUDIO=y`, and peripheral battery `..._BATTERY_LEVEL_FETCHING`/`..._PROXY`
- **config/corne.conf**: Power (idle 2 min, sleep 10 min, soft off), mouse keys (`CONFIG_ZMK_POINTING=y`), BLE split tuning. RGB and display disabled (no LEDs on this build)
- **config/corne.keymap**: Keymap in devicetree syntax — the source of truth
- **config/west.yml**: West manifest pointing to ZMK
- **README.md** (English), **README_ES.md** and **keymap_visual.md** (Spanish): layer diagrams must match the keymap; update all three when it changes
- **LATAM_KEYMAP.md**: US keycode → symbol produced on macOS Latin American (ISO); check it before adding a symbol
- **claudedocs/**: analyses and decisions (e.g. `homologacion-sofle.md`, parity with the user's Sofle QMK config in `../qmk-userspace-sofle`)

### Layers
| # | Layer | Type | Access |
|---|---|---|---|
| 0 | default | always on | — |
| 1 | lower (numbers, symbols) | momentary | hold LOWER thumb (`&mo 1`) |
| 2 | raise (operators, navigation) | momentary | hold RAISE thumb (`&mo 2`) |
| 3 | adjust (F-keys, BT, media, macOS macros, Studio unlock, soft off) | momentary | LOWER + RAISE (`&mo 3` on the opposite thumb in lower/raise) or hold ESC (`&lt_fast 3 ESC`) |
| 4 | mouse | toggle | RAISE + ESC corner or adjust J (`&tog 4`); exit with the corner (`&to 0`) |

### Rules Learned the Hard Way
- **Every layer must have exactly 42 bindings.** ZMK silently drops extras (only a `excess elements in array initializer` warning in the build log) and every binding after the extra one shifts to a different physical key.
- **Verify against the keymap, not the docs.** Before saying what a key does, read its binding (position → binding). Before a keymap PR, diff the physical behavior per layer before/after, emulating ZMK (first 42 bindings; `&trans` falls through to lower active layers) and list every changed key in the PR description.
- **Do not use `zmk,conditional-layers` for adjust**: it deactivates the then-layer on every layer change unless all if-layers are active, which kills `&mo 3` from ESC.
- **Symbols needing Option use `LA(...)` (left Option), never `RA(...)`**: Ghostty has `macos-option-as-alt = right`, so right Option arrives as Alt. The right thumb stays `RALT` for Alt+hjkl in Zellij.
- Mouse (layer 4) is the highest layer, so while it is on it shadows lower/raise/adjust on the keys it defines; its right thumbs are clicks (no Enter/RAISE inside mouse, accepted trade-off).

### Common ZMK Behaviors Used
- `&kp`: Key press
- `&mo` / `&tog` / `&to`: Momentary / toggle / absolute layer
- `&lt_fast`: Custom hold-tap (tap-preferred, 150 ms) used for ESC/adjust
- `&smart_shft`: Custom hold-tap (hold = Shift, tap = sticky Shift)
- `&bspc_del`: Mod-morph (Backspace, Shift = Delete)
- `&caps_word` (F+J combo), `&key_repeat`
- `&mkp` / `&mmv` / `&msc`: Mouse click / move / scroll
- `&bt`: Bluetooth commands (`BT_CLR` clears only the selected profile)
- `&studio_unlock`, `&soft_off`
