# Correcciones LOWER - Símbolos LATAM

## Cambios aplicados:

### Fila superior (números/símbolos):
- `\` → Cambiado de BSLH a NUBS (Non-US Backslash)
- `!` → Cambiado de N1 a EXCL (exclamación directa)

### Fila media (símbolos):
- `(` → Cambiado de LPAR a N8 (Shift+8 = ()
- `)` → Cambiado de RPAR a N9 (Shift+9 = ))
- `` ` `` → Cambiado de LBKT a GRAVE (acento grave)
- `=` → Cambiado de N0 a EQUAL (igual directo)

## Si el backslash sigue sin funcionar:

Opciones para probar:
1. Cambiar NUBS por INT1
2. Cambiar NUBS por INT2  
3. Usar RA(MINUS) para AltGr+-
4. Mapear manualmente el keycode

## Mapa LOWER actualizado:
```
TAB   7   8   9   /   *  |  '   ¿   \   ¿   !  BKSP
SHIFT 4   5   6   +   -  |  (   )   `   ´   =   `
CTRL  1   2   3   .   0  |      <   >   |   _  DEL
```