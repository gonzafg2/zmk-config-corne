# 🔍 Búsqueda del Acento Perdido - LATAM

## Intentos realizados:
1. ❌ `SQT` → Produce `-`
2. ❌ `RBKT` → Produce `+`  
3. ❌ `GRAVE` → Produce `|`
4. 🔄 `BSLH` → Probando ahora...

## Si BSLH no funciona, próximos intentos:

### Opción A: Probar más keycodes
```c
&kp EQUAL    // Tecla =
&kp MINUS    // Tecla -
&kp NUBS     // Non-US Backslash
&kp NUHS     // Non-US Hash
&kp INT1     // International 1
```

### Opción B: Mapeo directo con modificador
```c
&kp RA(E)    // AltGr+E (acento agudo en algunos layouts)
```

### Opción C: Buscar en tu teclado físico
En tu MacBook con layout LATAM:
1. ¿Qué tecla física produces el acento ´?
2. ¿Está en la fila superior, cerca de números?
3. ¿O está cerca de Enter?

## 🎯 Cambios aplicados en este push:

1. **Acento**: `GRAVE` → `BSLH` (nueva prueba)
2. **Slash /**: `N7` → `SLASH` (keycode directo)
3. **Guión -**: `SQT` → `FSLH` (debería producir -)

## 🧪 Prueba rápida:
Intenta escribir: "José María está aquí"
- Si funciona: ¡Encontramos el acento! 🎉
- Si no: Dime qué carácter produce BSLH