# Mapa de teclas visual — Corne

Fuente de verdad: `config/corne.keymap`. Estos diagramas son los mismos de `README.md`; si cambias el keymap, actualiza ambos.
Los símbolos asumen macOS con layout **Latin American** y tipo de teclado **ISO** (ver `README.md`). Casilla vacía = la misma tecla de la capa normal.

## Capa 0 — Normal (siempre activa)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │BSDL*│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHFT†│  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  Ñ  │  ´  │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ GUI │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  -  │ESC‡ │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │CTRL │LOWER│ SPC │   │ ENT │RAISE│RALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

*BSDL: tap = Backspace | Shift + tap = Delete
†SHFT: tap = Shift de un solo uso (solo la siguiente tecla) | mantener = Shift sostenido (smart shift)
‡ESC: tap = Escape | mantener 150 ms = capa Adjust
F + J a la vez: Caps Word (mayúsculas hasta espacio, Enter u otra tecla que no sea letra)
```

## Capa 1 — Lower (transitoria: mantener LOWER)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  7  │  8  │  9  │  /  │  *  │   │  (  │  )  │  \  │  !  │  ?  │BSDL │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHFT │  4  │  5  │  6  │  +  │  -  │   │  {  │  }  │  ~  │  '  │  "  │  `  │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ GUI │  1  │  2  │  3  │  .  │  0  │   │  [  │  ]  │  <  │  >  │  |  │ DEL │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │CTRL │     │ SPC │   │ ENT │ ADJ │RALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

ADJ = capa Adjust (mantener junto con LOWER)
```

## Capa 2 — Raise (transitoria: mantener RAISE)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  !  │  @  │  #  │  $  │  %  │   │     │ RPT │     │     │ +=  │BSDL │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHFT │  ^  │     │  &  │ &&  │ ||  │   │  ←  │  ↓  │  ↑  │  →  │ -=  │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ GUI │ =>  │ ... │ ==  │ !== │ === │   │HOME │PG_DN│PG_UP│ END │     │MOUSE│
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │CTRL │ ADJ │ SPC │   │ ENT │     │ALTGR│
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

RPT = repetir la última tecla
MOUSE = activa la capa mouse (mantener RAISE + tocar la esquina)
ADJ = capa Adjust (mantener junto con RAISE)
```

## Capa 3 — Adjust (transitoria: LOWER + RAISE, o mantener ESC)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │   │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ BT0 │ BT1 │ BT2 │ BT3 │ BT4 │BTCLR│   │CLEAR│MOUSE│UNLCK│     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ OFF │SCR1 │SCR2 │SCR3 │LOCK │FORCE│   │VOL+ │VOL- │MUTE │PREV │NEXT │PLAY │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │CTRL │     │ SPC │   │ ENT │     │RALT │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

OFF = apagado total (mantener 2 s); se despierta con el botón reset del nice!nano
SCR1/SCR2/SCR3 = capturas macOS (⌘⇧3 / ⌘⇧4 / ⌘⇧5)
LOCK = bloquear pantalla (⌘⌃Q) | FORCE = forzar salida (⌘⌥Esc)
CLEAR = volver a la capa normal | MOUSE = activa la capa mouse | UNLCK = desbloquear ZMK Studio
BT0-BT4 = perfiles Bluetooth | BTCLR = borrar el perfil actual
```

## Capa 4 — Mouse (permanente: RAISE + esquina, o Adjust → MOUSE; salir con EXIT)
```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │   │     │     │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │   │ M_← │ M_↓ │ M_↑ │ M_→ │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │   │ S_← │ S_↓ │ S_↑ │ S_→ │     │EXIT │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                   │     │     │     │   │LCLK │RCLK │MCLK │
                   └─────┴─────┴─────┘   └─────┴─────┴─────┘

M_←↓↑→ = mover el mouse (H/J/K/L) | S_←↓↑→ = scroll
LCLK/RCLK/MCLK = clic izquierdo/derecho/central (pulgares derechos)
EXIT = volver a la capa normal
```

## Notas

- Adjust con LOWER + RAISE se mantiene hasta soltar el pulgar que apretaste **segundo**.
- Al entrar a la capa mouse con RAISE + esquina, suelta RAISE: mientras lo mantengas, H/J/K/L mueven el mouse.
- Dentro de la capa mouse los pulgares derechos son clics: no hay ENTER, RAISE ni LOWER + RAISE. Sal con EXIT.
- `@` y `~` usan Option **izquierda** (`LA(...)`); el pulgar RALT es Option derecha, que Ghostty trata como Alt (Alt+h/j/k/l en Zellij).
