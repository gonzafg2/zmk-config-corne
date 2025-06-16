# 🔧 Cambios Críticos Aplicados - LATAM V2

## ✅ 1. CTRL ↔ SHIFT Intercambiados (¡Por fin!)
- **SHIFT** ahora en HOME ROW (junto a A)
- **CTRL** ahora en BOTTOM ROW (junto a Z)
- Aplicado en TODAS las capas

## ✅ 2. Acento ´ - Nueva Ubicación
- Cambiado de `RBKT` (que produce +) a `GRAVE`
- Ahora debería producir el acento correcto
- **PRUEBA**: Escribe "José", "María", "está"

## ✅ 3. Símbolos LOWER Corregidos

### Numpad (Izquierda):
```
7  8  9  /  *
4  5  6  +  -
1  2  3  .  0
```
Cambios aplicados:
- `/` ahora usa N7 (Shift+7 = /)
- `+` ahora usa RBKT (produce +)
- `-` ahora usa SQT (produce -)

## ✅ 4. RGB Removido
- Quitados controles RGB en ADJUST ya que no tienes LEDs

## 📋 Mapa Actualizado

### DEFAULT
```
TAB   Q   W   E   R   T  |  Y   U   I   O   P  BKSP
SHIFT A   S   D   F   G  |  H   J   K   L   Ñ   ´   ← ACENTO AQUÍ
CTRL  Z   X   C   V   B  |  N   M   ,   .   -  ESC
         GUI LOWER SPC   | ENT RAISE ALT
```

### LOWER (Numpad + Símbolos)
```
TAB   7   8   9   /   *  |  '   ¿   \   ¿   !  BKSP
SHIFT 4   5   6   +   -  |  (   )   `   +   =   `
CTRL  1   2   3   .   0  |      <   >   |   _  DEL
         GUI ___  SPC    | ENT ___ ALT
```

## 🧪 Pruebas Importantes

1. **Acento**: ¿Funciona escribir con tildes?
2. **Shift/Ctrl**: ¿Están en las posiciones correctas ahora?
3. **Símbolos LOWER**: ¿Salen / + - correctamente?

## ⚠️ Si el acento aún no funciona:

El acento podría estar en otra tecla. Opciones para probar:
1. Cambiar `GRAVE` por `BSLH`
2. Cambiar `GRAVE` por `NUBS` 
3. Mapear directamente con un keycode específico

## 🎯 Siguiente paso:
Prueba estos cambios y dime:
- ¿Funciona el acento?
- ¿Están bien Ctrl/Shift?
- ¿Qué otros símbolos fallan?