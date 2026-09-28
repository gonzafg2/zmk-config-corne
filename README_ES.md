# Configuración ZMK Corne - Layout Español

## ⚠️ Advertencia Importante - Batería y RGB

**Con RGB al 100% y batería de 110mAh:**
- ⚡ Duración estimada: **10-15 minutos**
- 🔋 Necesitarás cargar el teclado **varias veces al día**
- 💡 Recomendación: Usa RGB_TOG para apagar cuando no necesites

### Duración aproximada según brillo:
- 100% brillo: ~12 minutos
- 50% brillo: ~25 minutos  
- 20% brillo: ~1 hora
- 10% brillo: ~2 horas
- RGB apagado: ~1-2 meses

## 🔤 Mapeo de Símbolos - Español

### Configuración del Sistema Operativo
Este keymap envía códigos US que tu OS interpreta según el layout configurado:
- **macOS**: Preferencias > Teclado > Fuentes de entrada > Español (o Español - ISO)
- **Windows**: Configuración > Hora e idioma > Idioma > Español
- **Linux**: setxkbmap es

### Tabla de Conversión Keymap → Símbolo Español

| Tecla en Keymap | Keycode ZMK | Salida ES España | Salida ES LATAM |
|-----------------|-------------|------------------|------------------|
| ; | SEMI | ñ | ñ |
| ' | SQT | ´ (acento muerto) | ´ (acento muerto) |
| / | FSLH | - | - |
| \ | BSLH | \ | \ |
| [ | LBKT | ` | [ |
| ] | RBKT | + | ] |
| ` | GRAVE | < | < |

### Símbolos con AltGr (RAISE layer tiene ALTGR)
- **@ arroba**: AltGr + 2 (España) / AltGr + Q (LATAM)
- **# numeral**: AltGr + 3 (España) / Shift + 3 (LATAM)
- **€ euro**: AltGr + E (ambos)
- **\\ backslash**: Mapeado directamente en LOWER / AltGr + - (varía)

## ⌨️ Layout de Capas

### Capa 0 - DEFAULT
```
TAB   Q   W   E   R   T  |  Y   U   I   O   P  BKSP
SHFT  A   S   D   F   G  |  H   J   K   L   Ñ   ´
GUI   Z   X   C   V   B  |  N   M   ,   .   -  ESC
         CTRL LOWER SPC   | ENT RAISE RALT
```

### Capa 1 - LOWER (Numpad + Símbolos)
```
TAB   7   8   9   /   *  |  `   +   \   ¿   ¡  BKSP
SHFT  4   5   6   +   -  |  (   )   {   }   =   <
GUI   1   2   3   .   0  |      <   >   |   _  DEL
         CTRL ___  SPC    | ENT RAISE RALT
```

### Capa 2 - RAISE (Nav + Símbolos)
```
TAB   !   "   #   $   %  |  &   -   (   )   ?  BKSP
SHFT  ^   @   €   ~   °  | ←   ↓   ↑   →   ¨   +
GUI   --- --- --- --- ---|HOME PGDN PGUP END INS ESC
         CTRL LOWER SPC   | ENT ___ ALTGR
```

### Capa 3 - ADJUST (Sistema + Control)
Activa con: **LOWER + RAISE simultáneamente**
```
F1    F2   F3   F4   F5  F6 | F7  F8  F9  F10 F11 F12
BT0   BT1  BT2  BT3  BT4 BTCLR|RGB BRI+ BRI- EFF SAT HUE
POWER SCR1 SCR2 SCR3 --- ---|VOL+ VOL- MUTE --- --- RESET
           CTRL ___  SPC      | ENT ___ RALT
```

## 🛠️ Funciones Especiales

### Control de Energía
- **POWER** (EP_TOG): Apaga/enciende poder externo y RGB
- **Idle**: 5 minutos sin actividad → reduce consumo
- **Sleep**: 15 minutos sin actividad → suspensión profunda

### Macros macOS Screenshots
- **SCR1**: Captura pantalla completa (⌘+⇧+3)
- **SCR2**: Captura área seleccionada (⌘+⇧+4)
- **SCR3**: Herramienta de captura (⌘+⇧+5)

### Control RGB (en ADJUST)
- **RGB**: Toggle ON/OFF
- **BRI+/BRI-**: Ajustar brillo
- **EFF**: Cambiar efecto (sólido/respiración/spectrum/swirl)
- **SAT**: Saturación
- **HUE**: Tono de color

### Bluetooth (en ADJUST)
- **BT0-BT4**: Seleccionar perfil 0-4
- **BTCLR**: Borrar TODOS los emparejamientos (¡usar con cuidado!)

## 📱 Proceso de Build y Flash

1. **Hacer cambios y push**:
   ```bash
   git add .
   git commit -m "Actualizar keymap español"
   git push origin feature/spanish-layout-enhanced
   ```

2. **Descargar firmware**:
   - Ve a GitHub → Actions → Último workflow
   - Descarga `firmware.zip`
   - Extrae los archivos .uf2

3. **Flashear**:
   - Conecta una mitad por USB
   - Doble click en botón reset → aparece como unidad USB
   - Copia `corne_left-nice_nano_v2.uf2`
   - Repite con la otra mitad y `corne_right-nice_nano_v2.uf2`

## 🔧 Solución de Problemas

### Si necesitas resetear configuración:
1. Flash `settings_reset-nice_nano_v2.uf2` en ambas mitades
2. Vuelve a flashear el firmware normal

### Si BT no conecta después de BT_CLR:
1. Elimina el teclado de TODOS tus dispositivos Bluetooth
2. Vuelve a emparejar desde cero

### Para máxima duración de batería:
1. Apaga RGB con RGB_TOG cuando no lo uses
2. Reduce brillo al mínimo necesario
3. Usa EP_TOG antes de transportar