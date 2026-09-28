# Configuración ZMK Corne — Layout Latin American (macOS)

Firmware ZMK para un Corne (crkbd) split con nice!nano v2. La fuente de verdad es `config/corne.keymap`; los diagramas de cada capa están en [`keymap_visual.md`](keymap_visual.md) (los mismos de `README.md`).

## 🔤 Configuración de macOS

El keymap envía códigos de teclado US y macOS los traduce según el layout configurado:

1. Fuentes de entrada: **Latin American**.
2. Ajustes → Teclado → "Cambiar tipo de teclado…" → presiona la tecla a la izquierda del `1` → elige **ISO (Europeo)**. Verifica que `<` y `>` salgan en Lower.

Los símbolos que necesitan Option (`@`, `~`, `\`, `` ` ``, `^`) usan Option **izquierda** (`LA(...)`). El pulgar RALT es Option **derecha**: Ghostty la trata como Alt (`macos-option-as-alt = right`), lo que permite Alt+h/j/k/l en Zellij.

## ⌨️ Capas

| Capa | Tipo | Cómo entras | Cómo sales |
|---|---|---|---|
| 0 Normal | Siempre activa | — | — |
| 1 Lower (números y símbolos) | Transitoria | Mantener pulgar LOWER | Soltar |
| 2 Raise (programación y navegación) | Transitoria | Mantener pulgar RAISE | Soltar |
| 3 Adjust (sistema y media) | Transitoria | LOWER + RAISE, o mantener ESC (150 ms) | Soltar (con LOWER + RAISE, el pulgar que apretaste segundo) |
| 4 Mouse | Permanente | RAISE + tocar la esquina ESC, o Adjust → MOUSE | EXIT (esquina) o CLEAR en Adjust |

- Mouse es la capa más alta: mientras está activa gana sobre Lower, Raise y Adjust en las teclas que define.
- Al entrar a mouse con RAISE + esquina, suelta RAISE.
- Dentro de mouse los pulgares derechos son clics: no hay ENTER, RAISE ni LOWER + RAISE.

## 🛠️ Funciones especiales

- **BSDL**: tap = Backspace, Shift + tap = Delete.
- **Smart shift** (experimental): tap = Shift de un solo uso, mantener = Shift sostenido.
- **Caps Word**: F + J a la vez; mayúsculas hasta espacio, Enter u otra tecla que no sea letra.
- **Repetir tecla**: Raise + U.
- **Operadores** (Raise): `&&`, `||`, `==`, `!==`, `===`, `=>`, `...`, `+=`, `-=`.
- **Adjust**:
  - F1–F12, volumen, mute, anterior/siguiente, play/pausa.
  - BT0–BT4: perfiles Bluetooth. BTCLR: borra el emparejamiento del perfil **seleccionado**.
  - CLEAR: vuelve a la capa normal. MOUSE: activa la capa mouse. UNLCK: desbloquea ZMK Studio.
  - SCR1/SCR2/SCR3: capturas (⌘⇧3 / ⌘⇧4 / ⌘⇧5). LOCK: bloquear pantalla (⌘⌃Q). FORCE: forzar salida (⌘⌥Esc).
  - OFF: apagado total manteniéndolo 2 s; se despierta con el botón reset del nice!nano.

## 🔋 Energía

- Idle a los 2 minutos y sueño profundo a los 10 minutos sin uso (`config/corne.conf`).
- Sin RGB ni pantalla en este build.
- Batería: la izquierda reporta la suya y la de la derecha (configurado en `build.yaml`). El menú Bluetooth de macOS muestra solo una; para ver ambas usa una app de barra de menú como [ZMK Battery Bar](https://github.com/itouuuuuuuuu/zmk-battery-bar) o [zmk-battery-center](https://github.com/kot149/zmk-battery-center). Requiere el Corne emparejado por Bluetooth con el Mac.
- Para transportarlo: Adjust → mantener OFF 2 s.

## 🎛️ ZMK Studio

Solo por USB en la mitad izquierda: abre [zmk.studio](https://zmk.studio) en Chrome o Edge y presiona UNLCK en Adjust. Lo que guardes en Studio queda en el teclado, no en el repo, y tiene prioridad sobre el keymap del firmware; para volver al keymap del repo usa "Restore Stock Settings".

## 📱 Build y flash

1. Push a GitHub: GitHub Actions compila (`build.yaml`).
2. Descarga el artifact `firmware` y extrae los `.uf2`:
   - `corne_left-nice_nano__zmk-zmk.uf2` (izquierda, con ZMK Studio)
   - `corne_right-nice_nano__zmk-zmk.uf2` (derecha)
   - `settings_reset-nice_nano__zmk-zmk.uf2`
3. Conecta una mitad por USB, doble clic en reset y copia su `.uf2` a la unidad que aparece.

Si solo cambió el keymap, basta con flashear la mitad izquierda (el keymap se procesa en la central).

## 🔧 Solución de problemas

- **Resetear configuración**: flashea `settings_reset` en ambas mitades, luego el firmware normal en cada una, y vuelve a emparejar el Bluetooth.
- **El mouse no se mueve por Bluetooth**: las teclas de mouse cambian el descriptor HID; olvida "Corne" en cada equipo, borra el perfil con BTCLR y vuelve a emparejar.
- **Capas pegadas**: CLEAR en Adjust.
