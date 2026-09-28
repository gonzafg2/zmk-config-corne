# Mapeo de keycodes para layout LATAM (macOS)

El keymap envía códigos de teclado US y macOS los traduce con el layout **Latin American** y tipo de teclado **ISO** (ver `README.md`). Esta tabla dice qué produce cada keycode que usa `config/corne.keymap`; los diagramas por capa están en `README.md` y `keymap_visual.md`.

Fuente de cada valor: los reportes de prueba de los commits `5e8b4b9` (SQT, BSLH, DQT, PIPE, GRAVE, QMARK, UNDER) y `b8ab404` (EQUAL, `LS(N0)`), el commit `35ebea3` (`LA(MINUS)` = `\`) y las etiquetas de `README.md` para el resto. "—" = el keymap no usa esa combinación.

## Teclas de símbolo

| Keycode ZMK | Sin Shift | Con Shift | Con Option izquierda (`LA`) | Dónde se usa |
|---|---|---|---|---|
| `SEMI` | ñ | — | — | Normal (Ñ) |
| `LBKT` | ´ (acento muerto) | — | — | Normal (´) |
| `RBKT` | + | — | ~ | Lower (`+`, `~`), macro `+=` |
| `SQT` | { | [ (`DQT`) | ^ | Lower (`{`, `[`), Raise (`^`) |
| `BSLH` | } | ] (`PIPE`) | `` ` `` | Lower (`}`, `]`, `` ` ``) |
| `MINUS` | ' | ? (`UNDER`) | \ | Lower (`'`, `?`, `\`) |
| `FSLH` | - | _ (`QMARK`, hoy sin uso) | — | Normal (`-`), Lower (`-`), macro `-=` |
| `GRAVE` | \| | — | — | Lower (`\|`), macro `\|\|` |
| `NUBS` (tecla ISO junto a Z) | < | > | — | Lower (`<`, `>`), macro `=>` |
| `EQUAL` | ¿ | — | — | No usado: por eso `=` es `LS(N0)` |
| `Q` | q | Q | @ | Raise (`@`) |

## Números con Shift

| `N1` | `N2` | `N3` | `N4` | `N5` | `N6` | `N7` | `N8` | `N9` | `N0` |
|---|---|---|---|---|---|---|---|---|---|
| ! | " | # | $ | % | & | / | ( | ) | = |

`!` se envía como `EXCL` (Shift + 1).

## Reglas

- Los símbolos que requieren Option usan Option **izquierda** (`LA(...)`), nunca `RA(...)`: Ghostty tiene `macos-option-as-alt = right` y la Option derecha llega como Alt.
- `=` siempre es `LS(N0)`; `EQUAL` produce `¿`.
- `*` usa `KP_MULTIPLY`.
- Si `<` y `>` salen distinto, revisa que macOS tenga el tipo de teclado ISO.
