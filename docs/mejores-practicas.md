# Mejores Prácticas - Estrategias Avanzadas

## Estructura de solicitudes profesionales

### El formato de "Contexto + Objetivo + Requisitos"

```
Contexto: Estoy trabajando en un módulo de autenticación en Node.js/Express
Objetivo: Necesito crear middleware para verificar JWT
Requisitos:
  - Debe retornar 401 si no hay token
  - Debe validar la firma del token
  - Debe extraer el payload y pasarlo a req.user
  - Debe usar async/await
```

Este formato proporciona claridad máxima a Copilot.

## Patrones de trabajo efectivos

### 1. Test-First Development con Copilot

```
/test genera pruebas exhaustivas para esta función
[revisas las pruebas]
/generate implementa la función
[ejecutas las pruebas]
```

### 2. Refactor en ciclos

Primero genera candidato:
```
/refactor mejora legibilidad
```

Luego itera:
```
/refactor pero sin usar lodash, usa métodos nativos de arrays
```

### 3. Documentación post-implementación

```
/doc añade JSDoc completo con tipos y ejemplos
```

## Gestión del contexto efectiva

### Abre archivos relacionados

Antes de usar inline chat, abre en tabs:
- Interfaz/tipos relacionados
- Implementaciones similares
- Dependencias que vas a usar

Esto enriquece dramáticamente el contexto.

### Mantén el archivo guardado

Un archivo guardado proporciona mejor contexto que uno sin guardar. Usa auto-save.

### Usa comentarios como especificación

```javascript
/**
 * Calcula el descuento aplicable basado en:
 * - Tier de cliente (bronze, silver, gold)
 * - Monto de compra
 * - Si es cliente nuevo (+10% extra)
 * Retorna: {discountPercent, finalAmount}
 */
function calculateDiscount(tier, amount, isNew) {
  // Aquí: /generate
}
```

## Validación antes de aceptar

Implementa una checklist mental:

- [ ] ¿Es el código legible?
- [ ] ¿Maneja edge cases?
- [ ] ¿Sigue convenciones del proyecto?
- [ ] ¿Tiene tests?
- [ ] ¿Está documentado?

No aceptes ciegamente.

## Seguridad en primer plano

### Nunca confíes ciegamente en:

- SQL queries (riesgo de inyección)
- Validación de inputs
- Código criptográfico
- APIs con credenciales

Siempre verifica manualmente en estos casos.

### Solicitudes de seguridad

```
/fix busca vulnerabilidades de seguridad
especialmente: inyección SQL, XSS, CSRF, autorización
```

## Optimización de prompts

### De malo a excelente

❌ Malo:
```
hazme una función de búsqueda
```

✅ Mejor:
```
necesito función de búsqueda en array de objetos
que busque en propiedades 'nombre' e 'email'
con búsqueda case-insensitive y soporte para múltiples términos
```

✅ Excelente:
```
necesito función searchUsers(users, query) que:
- Recibe array de {id, nombre, email, activo}
- Busca en 'nombre' e 'email' (case-insensitive)
- Soporta múltiples términos separados por espacio (AND logic)
- Retorna array filtrado ordenado por relevancia
- Retorna [] si query vacío
- Maneja null/undefined gracefully
```

## Patrones de delegación efectivos

### Qué SÍ delegues a Copilot:

- Boilerplate y scaffolding
- Tests básicos
- Documentación inicial
- Refactoring mecánico
- Traducción entre lenguajes

### Qué NO delegues:

- Decisiones de diseño complejas
- Lógica de negocio crítica
- Validación de seguridad
- Optimización crítica
- Código que no entiendes

## Iteración estratégica

### Cuando obtienes un resultado mediocre:

1. **Analiza qué falta:** ¿Especificidad? ¿Restricciones? ¿Contexto?
2. **Reformula completamente:** No repitas, cambia enfoque
3. **Proporciona ejemplos:** Input/output específicos
4. **Añade restricciones:** "Sin librerías externas", "Debe ser O(n)"
5. **Verifica entendimiento:** "¿Entiendes lo que necesito?"

### Cuando obtienes un buen resultado:

1. **Personaliza pequeños detalles**
2. **Verifica contra requirements**
3. **Añade comentarios propios**
4. **Crea tests si falta**

## Métricas de productividad

Mide tu mejora:

- **Tiempo de implementación:** ¿Bajó?
- **Cobertura de tests:** ¿Mejoró?
- **Calidad de código:** ¿Más limpio?
- **Documentación:** ¿Mejor documentado?
- **Seguridad:** ¿Menos vulnerabilidades?

## Antipatrones a evitar

❌ **No hagas:**
- Aceptar código sin leer
- Usar Copilot para lógica crítica sin validar
- Olvidar documentar qué hizo Copilot
- Implementar sin entender el código
- Confiar en Copilot para seguridad

✅ **Sí haz:**
- Lee siempre antes de aceptar
- Valida código crítico exhaustivamente
- Aprende de lo que genera Copilot
- Entiende cada línea
- Usa Copilot como helper, no reemplazo

---

**Anterior:** [Chat Lateral](chat-lateral.md)  
**Siguiente:** [FAQ](faq.md)
