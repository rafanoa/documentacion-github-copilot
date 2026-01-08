# Chat Lateral (Copilot Chat) - Conversaciones Amplias

## ¿Qué es Chat Lateral?

El chat lateral de GitHub Copilot es un panel en el side de VS Code que permite conversaciones más amplias, debates arquitectónicos, y exploración conceptual sin estar limitado al contexto inmediato del código.

**Atajo:** `Ctrl+K`

## Diferencias: Inline Chat vs Chat Lateral

| Aspecto | Inline Chat | Chat Lateral |
|---------|-------------|--------------|
| **Atajo** | Ctrl+I | Ctrl+K |
| **Ubicación** | Flotante sobre código | Panel lateral |
| **Contexto** | Archivo actual | Proyecto general |
| **Uso ideal** | Cambios rápidos | Decisiones arquitectónicas |
| **Flujo** | Transaccional | Conversacional |

## Casos de uso reales

### 1. Diseño de arquitectura

```
¿Cuál es el mejor enfoque para implementar caché en una aplicación Node.js?
Necesito soportar expiración automática y invalidación manual.
```

### 2. Decisiones técnicas

```
Estoy decidiendo entre usar Redux o Context API en React.
Mi app tiene estado compartido entre muchos componentes.
¿Cuál me recomiendas y por qué?
```

### 3. Aprendizaje de conceptos

```
Explícame qué es una closure en JavaScript con ejemplos prácticos
```

### 4. Planificación de features

```
Quiero implementar autenticación OAuth en mi aplicación.
¿Cuál es el flujo recomendado? ¿Qué librerías me sugieres?
```

## Características avanzadas

### Referencias de archivos

Puedes referenciar archivos específicos:
```
@archivo-nombre.ts
```

### Buscar en contexto

Usa `@` para traer contexto:
```
@package.json ¿Cuál es la estructura de mis dependencias?
```

### Conversación multi-turno

El chat mantiene contexto de la conversación anterior, permitiendo:
- Refinamientos progresivos
- Referencias a intercambios anteriores
- Debates continuos

## Tips de productividad

1. **Para debates largos:** Usa chat lateral
2. **Para cambios de código:** Usa inline chat
3. **Combina ambos:** Discute en lateral, implementa en inline
4. **Mantén contexto abierto:** Abre archivos relevantes en tabs

---

**Anterior:** [Inline Chat](inline-chat.md)  
**Siguiente:** [Mejores Prácticas](mejores-practicas.md)
