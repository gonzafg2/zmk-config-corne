# 🎹 ZMK Config for Corne Keyboard - Spanish LATAM Layout

This is a ZMK firmware configuration for a Corne (crkbd) split mechanical keyboard optimized for Spanish LATAM layout on macOS.

## ✨ Features

- **🇪🇸 Spanish LATAM Layout**: Full support for Spanish characters including ñ, accents, and special symbols
- **💻 Programming-focused layers**: Dedicated symbols and operators for coding
- **🍎 macOS Integration**: Screenshot shortcuts, media controls, and system functions
- **🔋 Power Management**: Optimized sleep and idle settings
- **📶 Bluetooth**: Multi-device support with 5 profiles

## ⚠️ Important Setup Note

⚠️ **For proper symbol mapping on macOS, you MUST configure your keyboard as ISO layout, not ANSI**

### macOS Keyboard Setup
1. Go to System Preferences → Keyboard
2. Click "Change Keyboard Type..."
3. When prompted, press the key to the left of "1" (should be °)
4. Select **ISO (European)** layout
5. Verify by typing: < > should work with NUBS key

## ⌨️ Keymap Overview

### 🏠 Base Layer (QWERTY)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │ BKSP│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHIFT│  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  Ñ  │  ´  │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│CTRL │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  -  │ESC* │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │ GUI │LOWER│ SPC │   │ ENT │RAISE│ ALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

*ESC: tap = ESC | hold (150ms) = Adjust layer
```

### 🔢 Lower Layer (Numbers & Spanish Symbols)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  7  │  8  │  9  │  /  │  *  │   │  (  │  )  │  \  │  !  │  ?  │ BKSP│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHIFT│  4  │  5  │  6  │  +  │  -  │   │  {  │  }  │  ~  │  '  │  "  │  `  │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│CTRL │  1  │  2  │  3  │  .  │  0  │   │  [  │  ]  │  <  │  >  │  |  │  _  │ DEL │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┴─────┘
                   │ GUI │     │ SPC │   │ ENT │     │ ALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

⚠️ Row 3 has 13 bindings (known firmware anomaly)
```

### 💻 Raise Layer (Programming & Navigation)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  !  │  @  │  #  │  $  │  %  │   │     │     │     │     │ +=  │ BKSP│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHIFT│  ^  │     │  &  │ &&  │ ||  │   │  ←  │  ↓  │  ↑  │  →  │ -=  │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│CTRL │ =>  │ ... │ ==  │ !== │ === │   │HOME │PG_DN│PG_UP│ END │     │     │ ESC │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┴─────┘
                   │ GUI │     │ SPC │   │ ENT │     │ALTGR│
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

⚠️ Row 3 has 13 bindings (known firmware anomaly)
```

### ⚙️ Adjust Layer (System & Media)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │   │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ BT0 │ BT1 │ BT2 │ BT3 │ BT4 │BTCLR│   │CLEAR│     │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ OFF │SCR1 │SCR2 │SCR3 │LOCK │FORCE│   │VOL+ │VOL- │MUTE │PREV │NEXT │PLAY │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │ GUI │     │ SPC │   │ ENT │     │ ALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

> [!TIP]
> **🔑 Accessing the Adjust Layer**
>
> There are 2 ways to activate this layer:
> 1. **Hold ESC** (bottom-right corner of base layer) for 150ms
> 2. **TAB + BACKSPACE combo** (press both simultaneously) — works from any layer
>
> ⚠️ Conditional layers (LOWER + RAISE) were disabled due to a bug with `mo` behaviors.

## 🎯 Special Functions

### 💻 Programming Operators (RAISE layer)
- `&&` - Logical AND
- `||` - Logical OR
- `==` - Equality
- `!==` - Strict inequality
- `===` - Strict equality
- `=>` - Arrow function
- `...` - Spread operator
- `+=` - Addition assignment
- `-=` - Subtraction assignment

### 🖥️ System Controls (ADJUST layer)
- **BT0-BT4**: Bluetooth profile selection
- **BTCLR**: Clear current Bluetooth profile
- **CLEAR**: Reset to base layer (emergency unstuck)
- **OFF**: Soft power off (hold 2s). Wake via reset button on the nice!nano
- **SCR1**: Full screenshot (Cmd+Shift+3)
- **SCR2**: Area screenshot (Cmd+Shift+4)
- **SCR3**: Screenshot tool (Cmd+Shift+5)
- **LOCK**: Lock screen (Cmd+Ctrl+Q)
- **FORCE**: Force quit (Cmd+Option+Esc)

### 🎵 Media Controls
- Volume Up/Down
- Mute
- Previous/Next Track
- Play/Pause

## 🔧 Configuration Details

### 🔋 Power Management
- **Idle timeout**: 2 minutes (low power, instant wake on keypress)
- **Sleep timeout**: 10 minutes (deep sleep, wake on keypress)
- **Soft Off**: Hold OFF key (2s) in ADJUST layer for full shutdown. Wake via nice!nano reset button
- **BLE optimized**: 0 dBm TX, 30-50ms connection intervals

### 📶 Bluetooth
- 5 profiles for multi-device support
- Experimental connection improvements enabled

### 🗂️ Layer Access
- **Lower**: Hold left thumb key
- **Raise**: Hold right thumb key
- **Adjust**: Hold ESC (bottom-right, 150ms) or TAB + BACKSPACE combo

## 🏗️ Building

This configuration uses GitHub Actions for automated builds. Push changes to trigger a new build and download the firmware artifacts.

## 📥 Installation

1. Download the firmware files from GitHub Actions artifacts
2. Put keyboard in bootloader mode (double-tap reset)
3. Copy the appropriate `.uf2` file to the keyboard
   - `corne_left-nice_nano_v2.uf2` for left half
   - `corne_right-nice_nano_v2.uf2` for right half

## 🧪 Testing & Verification

### 🇪🇸 Spanish Characters Test
Test these key combinations to verify LATAM layout:
```
' + vowel = á é í ó ú
Shift + ' = ¨ (for ü)
AltGr + ? = ¿
Shift + 1 = ¡
< and > = NUBS and Shift+NUBS
```

### 💻 Programming Operators Test (RAISE layer)
Verify these macros produce correct output:
- `&&` - Logical AND
- `||` - Logical OR
- `=>` - Arrow function
- `==` - Equality
- `!==` - Strict inequality
- `===` - Strict equality
- `+=` - Addition assignment
- `-=` - Subtraction assignment
- `...` - Spread operator

### 🔀 Layer Switching Test
1. Test ESC layer-tap: Hold ESC for 150ms → ADJUST layer
2. Test combo: TAB + BSPC simultaneously → ADJUST layer
3. Verify no stuck layers after multiple activations

## 🚨 Troubleshooting

If layers get stuck, use the **CLEAR** button in ADJUST layer or the TAB+BACKSPACE combo to reset to base layer.

### 🔋 Transporting the Keyboard

To prevent battery drain during transport:

1. **Enter Adjust layer** (hold ESC or press TAB + BSPC combo)
2. **Hold OFF key** (bottom-left) for **2 seconds** — keyboard powers off completely
3. **To wake up**: Press the **reset button** on each nice!nano (small button on the PCB)

> [!NOTE]
> Both halves may need a reset button press. The right half (peripheral) may reconnect
> automatically when the left half (central) wakes, or may need its own reset press.

### ⏱️ Adjusting Layer-Tap Timing
If 150ms hold time for ESC→ADJUST feels too fast or slow, modify in `corne.keymap`:
```c
lt_fast: layer_tap_fast {
    tapping-term-ms = <150>;  // Adjust this value (100-250ms recommended)
}
```
