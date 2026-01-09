# Capítulo 5: Mejores Prácticas — Estrategias Avanzadas

## Introducción

Dominar Copilot es saber **cuándo** usarlo y **cómo** validar resultados.

## Estructura de Solicitudes

### El patrón Contexto + Objetivo + Requisitos

```
Contexto: [Tu proyecto]
Objetivo: [Qué necesitas]
Requisitos: [Detalles]
Restricciones: [Lo prohibido]
```

## Validación de Código

### Checklist Antes de Aceptar

- [ ] Legible
- [ ] Sigue convenciones
- [ ] Maneja errores
- [ ] Edge cases cubiertos
- [ ] Performance correcta
- [ ] Sin vulnerabilidades

### Nunca Confíes Ciegamente En

- SQL Queries (riesgo inyección)
- Criptografía
- Validación de entrada
- Datos sensibles

## Patrones de Trabajo

### Test-First Development

1. Especificar con tests
2. `/ test` crea suite
3. `/generate` implementa
4. Ejecuta tests

### Refactoring en Ciclos

- Turno 1: mejora legibilidad
- Turno 2: sin librerías
- Turno 3: extrae funciones

## Delegación Inteligente

### ✅ SÍ Delega

- Boilerplate
- Tests básicos
- Documentación
- Refactoring mecánico

### ❌ NO Delegues

- Decisiones críticas
- Lógica de negocio
- Seguridad sensible

## Conclusión

Los mejores desarrolladores saben **cuándo** usar Copilot.

---

**Anterior:** [Instructions](instructions.md)  
**Siguiente:** [FAQ](faq.md)
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
