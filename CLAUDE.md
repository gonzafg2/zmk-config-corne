# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a ZMK firmware configuration repository for a Corne (crkbd) split mechanical keyboard using nice!nano v2 controllers. ZMK (Zephyr Mechanical Keyboard) is an open-source keyboard firmware built on the Zephyr RTOS.

## Key Commands

### Building Firmware
- **GitHub Actions**: Push changes to trigger automatic builds via `.github/workflows/build.yml`
- **Local builds**: Requires ZMK toolchain setup (west, Zephyr SDK)
  ```bash
  west build -p -b nice_nano_v2 -- -DSHIELD=corne_left
  west build -p -b nice_nano_v2 -- -DSHIELD=corne_right
  ```

### Firmware Files
After successful GitHub Actions build:
- Download artifacts from Actions tab
- Flash `corne_left-nice_nano_v2.uf2` to left half
- Flash `corne_right-nice_nano_v2.uf2` to right half
- Flash `settings_reset-nice_nano_v2.uf2` if needed to reset settings

## Architecture & Structure

### Configuration Files
- **build.yaml**: Defines build matrix for GitHub Actions (boards/shields combinations)
- **config/corne.conf**: Hardware configuration (RGB, display, power settings)
- **config/corne.keymap**: Keymap definition using devicetree syntax
  - Layer 0: Default QWERTY layout
  - Layer 1: Lower (numbers, bluetooth controls, navigation)
  - Layer 2: Raise (symbols)
- **config/west.yml**: West manifest pointing to ZMK repository

### Key Technical Details
- Uses devicetree bindings for keymap configuration
- Bluetooth profiles configured via `bt` behaviors (BT_SEL, BT_CLR)
- Power management: 10min sleep timeout, 2min idle timeout
- RGB underglow disabled but configured for 27 LEDs if enabled
- Display support disabled but available

### Modifying Keymaps
1. Edit `config/corne.keymap` using ZMK key codes
2. Layer switching uses `&mo` (momentary) behavior
3. Bluetooth commands use `&bt` behavior
4. Test changes by pushing to GitHub and downloading built firmware

### Common ZMK Behaviors
- `&kp`: Key press
- `&mo`: Momentary layer
- `&lt`: Layer-tap
- `&mt`: Mod-tap
- `&bt`: Bluetooth commands