# Capítulo 6: Preguntas Frecuentes — Troubleshooting y Respuestas

## Preguntas Generales

### ¿Copilot puede reemplazar programadores?

No. Copilot es un amplificador de productividad que requiere:
- Dirección clara
- Validación de código
- Decisiones arquitectónicas
- Pensamiento crítico

Programadores + Copilot = extraordinarios. Copilot solo = código mediocre.

### ¿Cuál es el costo?

- **Prueba gratuita:** 2 meses para nuevos usuarios
- **Copilot Individual:** $10/mes o $100/año
- **Copilot Pro:** $20/mes (más límites)
- **Copilot for Business:** Administrado por tu organización

### ¿Puedo usar Copilot offline?

No. Copilot requiere conexión constante a servidores de GitHub.

### ¿Mis archivos se envían a GitHub?

Sí. Fragmentos de código necesarios para generar sugerencias se envían a GitHub. Lee la política de privacidad para detalles específicos.

## Problemas Técnicos Comunes

### Problema: No recibo sugerencias

**Soluciones:**
1. Verifica que Copilot esté habilitado en Settings
2. Confirma que estás autenticado (`Ctrl+Shift+P` > `Copilot: Status`)
3. Reinicia VS Code
4. Verifica tu conexión a Internet

### Problema: Las sugerencias son malas

**Causas comunes:**
- Tu solicitud es demasiado vaga
- Falta contexto en el archivo
- No has guardado recientemente
- La tarea es muy compleja

**Solución:** Sé más específico. Proporciona más contexto. Abre archivos relacionados en tabs.

### Problema: Copilot sugiere código muy lentamente

**Intenta:**
1. Cerrar extensiones innecesarias
2. Reiniciar VS Code
3. Verificar conexión de red
4. Revisar si tu máquina está sobrecargada (revisor de tareas)

### Problema: El código generado tiene bugs

Esto es normal. Siempre:
1. Lee el código antes de aceptar
2. Ejecuta tests
3. Prueba edge cases
4. Itera si es necesario

### Problema: Conflicto con linter/formatter

Si Copilot sugiere código que tu linter rechaza:

```
/refactor pero respetando reglas de [tu-linter-name]
```

## Seguridad y Privacidad

### ¿Copilot sugiere código con vulnerabilidades?

Puede suceder. Siempre verifica:
- Inyección SQL
- XSS
- CSRF
- Autorización

Usa `/fix` pero valida manualmente.

### ¿Debo preocuparme por privacidad?

Considera:
- No compartas credenciales o tokens en chat
- No pongas API keys en solicitudes
- No solicites ayuda con datos sensibles
- Trata a Copilot como compañero de trabajo público

### ¿Cómo manejo código sensible?

Para código que requiere confidencialidad máxima:
1. No uses Copilot
2. O usa Copilot for Business con política clara
3. Revisa logs de qué enviaste

## Uso Empresarial

### ¿Puedo usar Copilot en código propietario?

Sí, con Copilot for Business. Consulta con tu departamento legal.

### ¿Cómo compartir Copilot en el equipo?

Opciones:
1. **Licencias individuales:** Cada developer su propia licencia
2. **Copilot for Business:** Gestiónalo desde GitHub organization
3. **GitHub Enterprise:** Para empresas grandes

### ¿Se entrena Copilot con mi código?

Depende del plan:
- **Copilot Individual:** Consulta términos
- **Copilot Pro:** Mejor privacidad
- **Copilot for Business:** Política empresarial clara

## Técnicas Avanzadas

### ¿Cómo hago Copilot más preciso?

1. **Sé específico:** Detalles > generalidades
2. **Proporciona contexto:** Abre archivos relacionados
3. **Guarda archivo:** Siempre antes de usar
4. **Comenta intenciones:** Ayuda a Copilot a entender
5. **Itera:** Refina solicitudes basado en respuestas

### ¿Cómo debuggeo con Copilot?

```
/fix identifica el bug en este código
[Copilot sugiere problema]
/test genera tests para evitar este bug
```

### ¿Puedo generar documentación?

Sí:
```
/doc genera documentación completa con ejemplos
```

Resultado: ~80% de lo que necesitas. Personaliza el 20% restante.

### ¿Cómo genero tests completos?

```
/test crea pruebas exhaustivas incluyendo:
- Casos felices
- Edge cases
- Manejo de errores
- Valores null/undefined
```

## Limitaciones

### ¿Cuáles son las limitaciones de Copilot?

**Contexto limitado:** No ve toda tu codebase, solo archivos abiertos  
**Complejidad:** Puede fallar con lógica muy compleja  
**Novedad:** Patrones muy recientes podrían no estar en entrenamiento  
**Iteración:** A veces requiere múltiples turnos para perfeccionar  

### ¿Hay límites de rate?

Depende de tu plan:
- **Individual:** Generosos (cientos de completions/día)
- **Pro:** Más altos
- **Business:** Personalizado

## Decisiones Comunes

### ¿Debo usar Inline Chat o Chat Lateral?

**Inline Chat (`Ctrl+I`)**
- Cambios rápidos sobre código
- 1-2 turnos máximo
- Contexto del archivo actual

**Chat Lateral (`Ctrl+K`)**
- Debates arquitectónicos
- Multi-turno conversacional
- Decisiones técnicas importantes

### ¿Debo generar código o estudiar primero?

**Genera si:**
- Ya entiendes el patrón
- Solo necesitas implementación
- Código es boilerplate

**Estudia primero si:**
- Patrón es nuevo para ti
- Lógica es crítica
- Necesitas profundidad conceptual

### ¿Cuándo debo hacer code review manual?

**Siempre** para:
- Código de seguridad sensible
- Lógica financiera crítica
- Cambios arquitectónicos
- Primeras contribuciones al proyecto

## Mejoras Futuras y Cambios

### ¿Cómo me mantengo actualizado?

- Revisa documentación oficial de GitHub Copilot periódicamente
- Sigue cambios en VS Code
- Experimenta con nuevas características
- Comparte descubrimientos con el equipo

### ¿Qué cambios esperar?

Copilot mejora constantemente:
- Modelos más potentes
- Mejor contexto workspace
- Integración con más IDEs
- Features de colaboración

## Recursos Útiles

- **Documentación oficial:** https://github.com/features/copilot
- **Comunidad:** GitHub Discussions
- **Feedback:** GitHub Issues

## Conclusión

Copilot es una herramienta en evolución. Los mejores usuarios son quienes entienden sus límites y lo usan conscientemente.

---

**Capítulo anterior:** [Mejores Prácticas](mejores-practicas.md)  
**Inicio:** [Índice](index.md)

**Última actualización:** Enero 2026

```
/test crea pruebas exhaustivas que cubran:
- Casos normales
- Edge cases
- Error handling
- Valores nulos/undefined
```

## Productividad

### ¿Cuánto tiempo gano realmente?

En promedio:
- **Generación de código:** 70% más rápido
- **Refactoring:** 60% más rápido
- **Testing:** 50% más rápido
- **Documentación:** 80% más rápido

Tu mileage puede variar.

### ¿Cómo maximizar productividad?

1. Aprende los atajos de teclado
2. Construye prompts efectivos
3. Valida código antes de aceptar
4. Usa en contextos donde Copilot es fuerte
5. Itera continuamente

### ¿Es malo confiar en Copilot?

No, si:
- Entiendes el código que genera
- Lo validas antes de usar
- No lo usas para decisiones críticas sin revisar

Es malo si:
- Aceptas ciegamente
- No entiendes qué hace
- Lo usas donde no pertenece

## Privacidad

### ¿Quién puede ver mi código?

- GitHub Copilot: Solo tú y Copilot
- Conversaciones: GitHub y OpenAI (parcialmente)
- Datos de telemetría: GitHub (anónimo)

Lee la política de privacidad completa.

### ¿Cómo proteger código sensible?

1. No lo pases a Copilot
2. O usa Copilot for Business
3. Revisa configuración de privacidad
4. Considera versión on-premise si disponible

## Soporte

### ¿Dónde reporto bugs?

- VS Code extension bugs: GitHub Copilot repo
- Problemas de autenticación: GitHub Support
- Problemas de feature: Feature requests en GitHub

### ¿Dónde encuentro ayuda?

- Documentación oficial: GitHub Copilot docs
- Comunidad: Stack Overflow con tag `github-copilot`
- Support oficial: GitHub Support

---

¿Tienes más preguntas? Consulta la documentación oficial o abre un issue en GitHub.

**Última actualización:** Enero 2026
