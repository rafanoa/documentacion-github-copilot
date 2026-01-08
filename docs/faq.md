# Preguntas Frecuentes (FAQ)

## Preguntas Generales

### ¿Copilot puede reemplazar programadores?

No. Copilot es un asistente que multiplica tu productividad, pero requiere:
- Dirección clara
- Validación de código
- Decisiones arquitectónicas
- Pensamiento crítico

Programadores + Copilot = súper productivos. Copilot solo = código mediocre.

### ¿Cuál es el costo?

- **Copilot Individual**: $10/mes o $100/año
- **Copilot Pro**: $20/mes (más límites)
- **Copilot for Business**: Planes empresariales

Se ofrece prueba gratuita de 2 meses.

### ¿Puedo usar Copilot offline?

No. Copilot requiere conexión constante a los servidores de GitHub.

### ¿Mis archivos se envían a GitHub?

Sí. El código necesario para completar sugerencias se envía a servidores de GitHub. Lee la política de privacidad para detalles.

## Problemas Comunes

### No recibo sugerencias

**Soluciones:**
1. Verifica que Copilot esté habilitado en Settings
2. Asegúrate de estar autenticado (Ctrl+Shift+P > Copilot: Status)
3. Reinicia VS Code
4. Verifica tu conexión a Internet

### Las sugerencias son malas

**Razones comunes:**
- Tu solicitud es muy vaga
- Falta contexto en el archivo
- No has guardado recientemente
- La tarea es muy compleja

**Solución:** Sé más específico y proporciona más contexto.

### Copilot sugiere código muy lentamente

Intenta:
1. Cerrar extensiones no usadas
2. Reiniciar VS Code
3. Verificar conexión de red
4. Revisar que tu máquina no esté sobrecargada

### El código generado tiene bugs

Esto es normal. Siempre:
1. Lee el código antes de aceptar
2. Ejecuta tests
3. Prueba edge cases
4. Itera si es necesario

### Conflict with linter/formatter

Si Copilot sugiere código que tu linter rechaza:

```
/refactor pero respetando las reglas de [tu-linter]
```

## Uso Empresarial

### ¿Puedo usar Copilot en código propietario?

Sí, con Copilot for Business. Consulta con tu departamento legal.

### ¿Cómo compartir Copilot en el equipo?

Opciones:
1. **Licencias individuales**: Cada desarrollador su propia licencia
2. **Copilot for Business**: Gestiónalo desde organización GitHub
3. **GitHub Enterprise**: Para empresas grandes

### ¿Se entrena Copilot con mi código?

Depende de tu plan:
- Copilot Individual: Consulta términos
- Copilot Pro: Mejor privacidad
- Copilot for Business: Política empresarial

## Seguridad

### ¿Copilot sugiere código con vulnerabilidades?

Puede suceder. Siempre verifica:
- Inyección SQL
- XSS
- CSRF
- Autorización

Usa `/fix` pero valida manualmente.

### ¿Debo preocuparme por mis datos?

- No compartas credenciales o tokens en chat
- No pongasAPI keys en solicitudes
- No solicites ayuda con datos sensibles

Trata a Copilot como un compañero de trabajo público.

### ¿Cómo manejo código sensible?

Para código que requiere confidencialidad máxima:
1. No uses Copilot
2. O usa Copilot for Business con política clara
3. Revisa logs de qué enviaste

## Técnicas

### ¿Cómo hago Copilot más preciso?

1. **Sé específico:** Detalles > generalidades
2. **Proporciona contexto:** Abre archivos relacionados
3. **Guarda archivo:** Siempre antes de usar
4. **Comenta intenciones:** Ayuda a Copilot a entender
5. **Itera:** Refina solicitudes basado en respuestas

### ¿Cómo debugging con Copilot?

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
