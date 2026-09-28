# Homologación con la Sofle — investigación y propuesta

Fecha: 2026-09-28
Estado: **investigación completa; acceso de la capa mouse IMPLEMENTADO (§6, rama `fix/raise-esc-mouse`); cascada de clicks DESCARTADA (§6); sabor del raise pendiente**
Base analizada: `config/corne.keymap` en `feature/ralt-cmd-ctrl-swap` (post PR #4: RALT en pulgar derecho + swap Cmd/Ctrl)
Referencia: `gonzafg2/qmk-userspace-sofle` (`keyboards/sofle/keymaps/gonzafg2/keymap.c`, `users/gonzafg2/gonzafg2.h`, `users/gonzafg2/gonzafg2.c`)

Exclusiones acordadas: iluminación (RGB) y bluetooth — fuera de alcance por definición.

---

## 1. Contexto estructural (condiciona toda la homologación)

La Sofle es QMK y tiene más hardware que el Corne:

| Recurso | Sofle | Corne |
|---|---|---|
| Filas de letras | 4 (incluye fila numérica) | 3 |
| Pulgares por lado | 5 | 3 |
| Encoders (con push) | 2 | 0 |
| Slot base | — | — |

Consecuencia: la Sofle reparte sus funciones en ~20+ slots; el Corne solo tiene **7 slots repurponsables en raise** (ver §4).

## 2. Ya homologado (verificado en ambos keymaps, no requiere acción)

- `RALT` en pulgar interior derecho (llegó al Corne con el PR #4; la Sofle lo tenía desde siempre)
- BSDL→DEL con shift (mod-morph `bspc_del` ≈ `GFG_BSDL` con su lógica `process_record_user`)
- ESC-hold → Adjust en la esquina derecha (`&lt_fast 3 ESC` ≈ `GFG_ESCAD = LT(_ADJUST, KC_ESC)`)
- Operadores `=>`, `==`, `===`, `!==`, `&&`, `||`, `+=`, `-=` (macros equivalentes)
- RPT (key repeat) sobre las flechas
- Flechas en HJKL + HOME/PGDN/PGUP/END alineadas debajo
- F-keys (Corne: adjust fila 1 | Sofle: lower fila 1 — ubicación distinta, ambas accesibles)
- Volumen/media en adjust (contenido equivalente: VOL±/MUTE/PREV/NEXT/PLAY)
- Screenshots/lock/force-quit como macros (Corne: adjust fila 3 | Sofle: raise fila 2 der "sobre cursores")
- **Capa mouse: el Corne YA la tiene** (capa 4, `CONFIG_ZMK_POINTING=y`, movimiento HJKL, scroll alineado debajo, exit en esquina, `&tog 4` en adjust ≈ `TGMOU` de la Sofle). Llegó con el commit 5d21720 (rama `feature/enhanced-behaviors`).

## 3. Mapa de diferencias (Sofle tiene → Corne le falta)

| # | Diferencia | Detalle |
|---|---|---|
| 1 | 5 operadores faltantes en raise | `>=`, `<=`, `??` (nullish coalescing), `?.` (optional chaining), `**` (pow). Secuencias ZMK decodificadas en §5 |
| 2 | Gestión de ventanas macOS en raise (9 teclas) | MCTL (⌃↑ Mission Control), APXP (⌃↓ App Expose), SPCL/SPCR (⌃←/⌃→ Spaces), ZM−/ZM+/ZM0 (⌘−/⌘+/⌘0 zoom), SPOT (⌘Space Spotlight), EMJI (⌘⌃Space emoji). El Corne no tiene ninguno |
| 3 | Ubicación de los macros mac | La Sofle los puso sobre las flechas en raise (a mano); el Corne los tiene en adjust |
| 4 | Mouse: entrada momentánea | Sofle: hold del push del encoder izq (`GFG_MUTM = LT(_MOUSE, KC_MUTE)`) + toggle en adjust. Corne: solo `&tog 4` |
| 5 | Mouse: layout en cascada | Sofle: clicks en fila 2 (BTN1/BTN3/BTN2), movimiento fila 3, scroll fila 4, columnas alineadas, **pulgares heredan base**. Corne: clicks en los pulgares derechos |
| 6 | Volumen "a mano" | Sofle: girar encoder base = volumen, push der = play/pause, tap push izq = mute. Corne: solo en adjust. **Limitación de hardware, no homologable** |

### Bug encontrado al mapear la capa mouse del Corne

Los clicks en los pulgares derechos tienen un costo oculto: dentro de la capa mouse,
el slot de RSE envía `&mkp RCLK` y el de RET envía `&mkp LCLK`. Consecuencias:
- **No se puede sostener RSE desde mouse** (el slot dejó de ser layer-switch)
- **Se pierde Enter dentro de mouse**

Mover los clicks a la fila 1 derecha (cascada Sofle) libera los pulgares y ambos
vuelven a heredar de base. Ver propuesta §6.

## 4. Restricción de espacio: los 7 slots de raise

Slots repurponsables del raise del Corne (hoy `&trans` que heredan la letra de base
— nadie tipea letras sosteniendo raise, costo de repurpose ≈ 0):

| Slot | Posición |
|---|---|
| Y, I, O | fila 1 derecha, sobre las flechas (← ↑ →) |
| S | fila 2 izquierda |
| ´ | fila 2 derecha (junto a `-=`) |
| / y º | fila 3 derecha (junto a END y ESC) |

14 candidatos (5 operadores + 9 window-mgmt/mac) para 7 slots → hay que priorizar.

## 5. Operadores faltantes: secuencias ZMK decodificadas

Decodificadas de `gonzafg2.c` (los `case GFG_*`), traducidas a keycodes ZMK con
el mismo enfoque posicional LATAM que ya usa este repo:

| Macro Sofle | Salida | Secuencia ZMK (`zmk,behavior-macro`) |
|---|---|---|
| `GFG_GTEQ` | `>=` | `&kp LS(NUBS) &kp LS(N0)` |
| `GFG_LTEQ` | `<=` | `&kp NUBS &kp LS(N0)` |
| `GFG_NULC` | `??` | `&kp LS(MINUS) &kp LS(MINUS)` |
| `GFG_OPTC` | `?.` | `&kp LS(MINUS) &kp DOT` |
| `GFG_POW` | `**` | `&kp KP_MULTIPLY &kp KP_MULTIPLY` |

Referencia de consistencia: `NUBS`/`LS(NUBS)` ya se usan en lower para `<`/`>`;
`LS(MINUS)` = `?` y `KP_MULTIPLY` = `*` (per already en lower). El patrón de macro
a seguir es el de `eq_op`/`and_op` existentes.

## 6. Propuesta (pendiente de decisión)

### Frente 1 — raise: dos sabores para 7 slots

**Sabor A — operadores primero** (recomendado para uso diario TS/Next.js):
- Y = `>=`, I = `<=`, O = `**`, S = `??`, ´ = `?.` (los 5 de §5)
- / = SPOT (`&kp LG(SPACE)`), º = MCTL (`&kp LC(UP)`)

**Sabor B — mac-nav primero** (más fiel a la ubicación de la Sofle):
- Y = SCRA (⌘⇧4), I = SCRT (⌘⇧5), O = LOCK (⌘⌃Q) — sobre las flechas, como la Sofle
- S = `??`, ´ = `?.`, / = SPOT, º = EMJI
- `>=`, `<=`, `**` quedan fuera de esta vuelta

Los 9 window-mgmt completos no caben; la tabla de §3-2 queda como pool de candidatos
para futuras vueltas (APXP, SPCL/SPCR, ZM±, ZM0, EMJI).

### Frente 2 — capa mouse: cascada + acceso raise+ESC

**Acceso DECIDIDO (2026-09-28)** — reemplaza la idea del combo Z+X/N+M:

| Acción | Teclas | Binding |
|---|---|---|
| Entrar (desde base/lower/raise) | RSE (pulgar medio der.) + esquina ESC | `&tog 4` en el slot de ESC de raise (hoy `&kp ESC` plano, sin uso real sosteniendo raise) |
| Salir (desde adentro) | la esquina sola | `&to 0` existente (EXIT) — sin cambios |
| Respaldo | adjust → tecla `MOUSE` (J, fila 2) | `&tog 4` existente — sin cambios |

Rationale del acceso:

- Entrada deliberada (acorde de 2 teclas, imposible de activar por accidente);
  salida de 1 tecla.
- Cualquier camino sale: adentro de mouse, raise+ESC resuelve a la capa mouse
  (número 4 gana sobre 2 en esa posición) y dispara su propio `&to 0` — no hay
  forma de quedar encerrado.
- Adentro de mouse la esquina no envía ESC (es EXIT); un ESC real se hace saliendo
  y usando el ESC de base.
- Único cambio de keymap: una línea — raise pos 35: `&kp ESC` → `&tog 4`.
- Descartado: triple toque. ZMK main sí tiene tap-dance, pero demora la primera
  acción hasta el timeout (ESC lento) y anidarlo sobre el `lt_fast 3` existente
  en esa misma tecla es el rincón frágil de behaviors.

**Cascada — DESCARTADA (2026-09-28):** el usuario prefiere los clicks en los pulgares derechos (ENT = LCLK, RSE = RCLK, RALT = MCLK). Costo aceptado: dentro de mouse no hay Enter ni RSE (ni LOWER+RAISE). Propuesta original, como referencia:

1. Clicks de los pulgares → fila 1 derecha (Y = LCLK, U = MCLK, I = RCLK, orden
   BTN1/BTN3/BTN2 de la Sofle). Movimiento fila 2 y scroll fila 3 quedan como están
   (ya alineados por columna). **Fix del bug de §3**: pulgares derechos vuelven a
   heredar base (RSE y RET recuperan su función dentro de mouse).
2. Opcional Sofle: EXIT también en la esquina superior derecha (hoy solo esquina inferior).

Nota de interacción: el acceso raise+ESC funciona igual con o sin cascada (la
salida resuelve a `&to 0` por precedencia de capas); la cascada solo revive el
pulgar RSE adentro de mouse, que hoy es `RCLK`.

### Frente 3 — volumen/media

Contenido ya homologado (§2). El acceso por encoder es ventaja de hardware de la
Sofle y no porta. Nada que hacer.

## 7. Exclusiones y no-propuestas

- RGB (Sofle adjust izquierda, `RM_*`) y BT (Corne adjust fila 2, `BT_*`): fuera por acuerdo.
- Tri-layer LWR+RSE→adjust de la Sofle: **no proponer** — este repo eliminó las
  conditional layers por un bug documentado con `mo` behaviors (comentario en
  `corne.keymap`). El acceso a adjust del Corne (hold ESC) ya cubre. *Actualización 2026-09-28: el bug era el desfase de 43 bindings (PR #5); LOWER+RAISE → Adjust volvió como `&mo 3` en el pulgar opuesto (PR #6) y se eliminó el combo TAB+BSDL.*
- F-keys a lower: diferencia estructural (el Corne no tiene fila numérica), dejar como está.
- ¿/¡ (aperturas LATAM en raise fila 2 de la Sofle): micro-diferencia, ya accesibles
  vía `?`/`!` con el layout; descartado salvo que se pidan explícito.

## 8. Estado de decisiones

- **Implementado (2026-09-28, rama `fix/raise-esc-mouse`)**: frente 2, acceso de la capa mouse — entrada
  **raise+ESC** (`&tog 4`), salida esquina (`&to 0`), respaldo adjust. Ver §6.
- Pendiente: frente 1 — sabor del raise (A/B/otro reparto de los 7 slots).
- **Descartado (2026-09-28)**: frente 2, cascada de clicks — los clicks quedan en los
  pulgares derechos por preferencia del usuario.
- Implementación: rama nueva apilada sobre `feature/enhanced-behaviors` (mismo
  flujo del PR #4), con docs (`README.md`, `README_ES.md`, `keymap_visual.md`)
  sincronizados y build del workflow para flashear.
