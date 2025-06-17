# Mapeo de Teclas para Layout LATAM

## 🔧 Cambios Aplicados

### Capa DEFAULT
- **Acento ´**: Ahora en la posición correcta (donde estaba ')
  - Antes: `&kp SQT` → producía `-`
  - Ahora: `&kp RBKT` → produce `´` ✅

### Capa LOWER - Símbolos Actualizados
```
Fila superior derecha:
- [ → Ahora con MINUS (produce ')  
- ] → Ahora con EQUAL (produce ¿)
- \ → BSLH (correcto)
- ¿ → EQUAL (produce ¿)
- ! → N1 (Shift+1 = !)

Fila media derecha:
- { → LBKT (produce `)
- } → RBKT (produce ´)  
- = → N0 (Shift+0 = =)
- ` → LBKT (produce `)
```

## 📋 Tabla de Referencia LATAM

### Keycodes US → Símbolos LATAM

| Keycode | Sin Shift | Con Shift | Con AltGr |
|---------|-----------|-----------|-----------|
| SEMI | ñ | Ñ | |
| RBKT | ´ (muerto) | ¨ (diéresis) | |
| LBKT | ` | ^ | |
| SQT | - | _ | |
| FSLH | - | _ | |
| MINUS | ' | ? | \ |
| EQUAL | ¿ | ¡ | |
| BSLH | } | ] | |

### Números con Shift en LATAM
- 1 → !
- 2 → "  
- 3 → #
- 4 → $
- 5 → %
- 6 → &
- 7 → /
- 8 → (
- 9 → )
- 0 → =

### Símbolos Especiales
- @ → AltGr + Q
- \ → AltGr + -
- | → AltGr + 1
- ~ → AltGr + 4
- [ → Necesitas explorar qué keycode lo produce
- ] → Necesitas explorar qué keycode lo produce

## ⚠️ Nota Importante

Los corchetes `[ ]` en LATAM pueden estar en posiciones no estándar. 
Prueba estas opciones:
1. Las teclas físicas donde esperarías [ ]
2. AltGr + otras teclas
3. Puede que necesites mapearlos explícitamente

## 🎯 Siguiente Paso

Si aún hay símbolos mal mapeados, indica:
1. ¿Qué símbolo esperabas?
2. ¿Qué símbolo apareció?
3. ¿En qué capa/posición?