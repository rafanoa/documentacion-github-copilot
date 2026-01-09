# Capítulo 7: Workflows de Copilot — Patrones Operacionales

## Introducción

Un **workflow de Copilot** es un patrón operacional repetible: una secuencia de pasos coordinados que Copilot ejecuta automáticamente para lograr un objetivo complejo. A diferencia de solicitudes puntuales, los workflows capturan procedimientos completos que tu equipo realiza frecuentemente.

Piensa en workflows como "comandos macro" para tu flujo de trabajo. En lugar de ejecutar 10 pasos manualmente cada vez, defines el workflow una sola vez y lo reutilizas indefinidamente.

Este capítulo enseña cómo estructurar, documentar e integrar workflows de Copilot en tu equipo.

## Parte 1: Fundamentos de Workflows

### ¿Qué es un Workflow?

Un workflow es:
- **Procedimiento documentado:** Pasos claros, secuenciales
- **Reutilizable:** Se ejecuta múltiples veces sin cambios
- **Confiable:** Produce resultados consistentes
- **Automatable:** Copilot puede ejecutarlo sin intervención
- **Equipable:** El equipo lo conoce y usa

**Ejemplo simple:**
```
Workflow: Crear Test Case Nuevo
1. Abrir archivo de tests existente
2. Copiar un test como plantilla
3. Renombrar con convención del proyecto
4. Reemplazar datos de test
5. Ejecutar para validar sintaxis
6. Vincular con Jira si es necesario
```

En lugar de hacer esto manualmente 20 veces por semana, lo documentas una vez y lo ejecutas con un comando.

### Cuándo Crear Workflows

Crea workflows para tareas que:
- Realizas **más de 2 veces por semana**
- Tienen **pasos claros y repetibles**
- Requieren **consistencia entre ejecuciones**
- Afectan a **múltiples personas del equipo**
- Tienen **riesgo de error humano**

**Ejemplos perfectos para workflows:**
- Crear nuevos tests
- Iniciar nuevo branch de desarrollo
- Hacer release del código
- Ejecutar auditorías de seguridad
- Crear structs/templates nuevos
- Migrar datos

**NO son candidatos para workflows:**
- Decisiones que requieren juicio crítico
- Problemas únicos/one-off
- Debugging complejo
- Exploraciones de nuevas tecnologías

## Parte 2: Estructura de Workflows Profesionales

### Plantilla Estándar

Documenta workflows con esta estructura:

```markdown
# Workflow: [Nombre Descriptivo del Workflow]

## Propósito
[Qué logra este workflow y para quién]

## Requisitos Previos
[Qué debe estar en lugar antes de ejecutar]

## Pasos

### Paso 1: [Descripción clara]
[Detalles específicos, comandos, validaciones]

### Paso 2: [Descripción clara]
[...]

## Validación
[Cómo sé que el workflow funcionó correctamente]

## Troubleshooting
[Errores comunes y cómo resolverlos]

## Variaciones
[Modificaciones comunes del workflow]

## Notas
[Contexto histórico, dependencias, cosas a evitar]
```

### Ejemplo: Workflow "Crear Test Class Nueva"

```markdown
# Workflow: Crear Test Class Nueva (JUnit 5)

## Propósito
Generar estructura de nueva clase de tests siguiendo 
convenciones del proyecto (Maven, Allure, JUnit 5, Jira integration)

## Requisitos Previos
- Proyecto abierto en VS Code
- Maven instalado y en PATH
- Jira connector ejecutándose (si quieres integración Jira)

## Pasos

### Paso 1: Definir ubicación y nombre
- Carpeta: src/test/java/com/project/tests/
- Nombre clase: [FeatureName]Tests.java
- Nombre paquete: com.project.tests.[feature]

### Paso 2: Usar template estándar
```java
package com.project.tests.feature;

import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import io.qameta.allure.Feature;
import io.qameta.allure.Story;

@DisplayName("Feature: [Description]")
@Feature("[Feature Name]")
public class FeatureTests {
    
    @DisplayName("[PROJ-XXX] Test case description")
    @Story("[Story Name]")
    @Test
    void testCaseName() {
        // Test implementation
    }
}
```

### Paso 3: Vincular con Jira
- Obtener @TestKey de Jira: PROJ-XXX
- Agregar anotación @TestKey("PROJ-XXX") a cada test
- MCP xray-connector mapeará automáticamente

### Paso 4: Validar sintaxis
```bash
mvn clean compile -pl api-test
```

### Paso 5: Crear primer test
Usar workflow "Crear Test Nuevo"

## Validación
✅ Archivo creado en ubicación correcta  
✅ Compila sin errores (mvn compile)  
✅ Allure reconoce la clase (@Feature funciona)  
✅ Jira mapping automático funciona  

## Troubleshooting

**Problema:** "Package declaration doesn't match folder"
- **Solución:** Verifica estructura de carpetas vs nombre de paquete

**Problema:** "@TestKey anotación no reconocida"
- **Solución:** Asegúrate de que TestKeyExtension está en classpath

## Variaciones

**Con Allure Stories:**
- Agrega @Story("nombre") para subtemas
- Agrupa tests relacionados bajo misma Story

**Sin Jira integration:**
- Omite @TestKey
- Usa solo @Test, @DisplayName, @Feature

## Notas
- El proyecto sigue convención Maven: src/test/java
- Jira keys deben existir previamente
- xray-connector convierte @TestKey a test_key en JUnit XML
```

## Parte 3: Integración con Equipo

### Documentación de Workflows Equipo

Crea archivo `WORKFLOWS.md` en la raíz del proyecto:

```markdown
# Workflows Disponibles del Equipo

## Categorías

### 🧪 Testing
- [Crear Test Class Nueva](#crear-test-class-nueva)
- [Ejecutar Smoke Tests](#ejecutar-smoke-tests)
- [Auditar Coverage](#auditar-coverage)

### 🔀 Git & Versioning
- [Iniciar Nueva Rama](#iniciar-nueva-rama)
- [Crear Pull Request](#crear-pull-request)
- [Sincronizar Rama](#sincronizar-rama)

### 📦 Release & Deployment
- [Preparar Release](#preparar-release)
- [Deploy a Staging](#deploy-a-staging)

---

## Crear Test Class Nueva

[Incluye workflow completo con pasos]

## Ejecutar Smoke Tests

[Incluye workflow completo]

...
```

Todos en el equipo pueden:
- Consultar workflows disponibles
- Ejecutarlos sin dudar
- Reportar mejoras

### Invocación de Workflows

**Opción A: Slash Command (Preferred)**
```
/crear-test-class-nueva
/ejecutar-smoke-tests
/iniciar-nueva-rama
```

**Opción B: Natural Language**
```
Quiero crear una nueva clase de tests
Necesito ejecutar los smoke tests
Voy a iniciar una nueva rama de desarrollo
```

Copilot entiende ambas formas e invoca el workflow correcto.

## Parte 4: Ejemplos del Mundo Real

### Workflow: "Ejecutar Smoke Tests"

**Contexto:** Proyecto Maven con JUnit 5, tests marcados con `@Tag("smoke")`

```markdown
# Workflow: Ejecutar Smoke Tests

## Propósito
Ejecutar suite rápida de smoke tests para validación inicial

## Pasos

### Paso 1: Limpiar build anterior
```bash
cd code
mvn clean
```

### Paso 2: Ejecutar tests con @Tag("smoke")
```bash
mvn -pl api-test test -Dgroups=smoke
```

### Paso 3: Presentar resultados
- Total tests ejecutados
- Pasaron / Fallaron
- Duración total
- Logs de errores si hay fallos

## Validación
✅ BUILD SUCCESS  
✅ Ningún test en error  
✅ Reporte Maven visible  

## Troubleshooting

**Problema:** "No tests found with tag=smoke"
- **Solución:** Verifica que tests tengan @Tag("smoke")

**Problema:** "mvn: command not found"
- **Solución:** Maven no en PATH, instala o actualiza variable
```

### Workflow: "Iniciar Nueva Rama"

**Contexto:** Proyecto Git con convención `TYPE/descripcion-corta`

```markdown
# Workflow: Iniciar Nueva Rama

## Propósito
Crear nuevo branch para desarrollo siguiendo convenciones

## Pasos

### Paso 1: Verificar estado
```bash
git status
```
Si hay cambios sin commit, pausar y pedir que guarde primero.

### Paso 2: Ir a main y sincronizar
```bash
git checkout main
git pull origin main
```

### Paso 3: Pedir nombre de rama
```
Convention: TYPE/descripcion

TYPE = feature | bugfix | hotfix | docs | refactor
```

### Paso 4: Crear y cambiar a rama
```bash
git checkout -b feature/nueva-funcionalidad
```

### Paso 5: Confirmar
```
Rama lista. Comenzar a codificar.
```

## Validación
✅ `git branch` muestra rama actual correcta  
✅ `git log` muestra commits de main  

## Troubleshooting

**Problema:** "Your branch is behind origin/main"
- **Solución:** Ejecuta `git pull origin main` primero

**Problema:** "Branch already exists"
- **Solución:** Elige otro nombre, la rama existe
```

### Workflow: "Crear Test Nueva"

**Contexto:** Integración con Jira, genera test method

```markdown
# Workflow: Crear Test Nueva (Jira-linked)

## Propósito
Agregar nuevo test method a clase existente con mapping Jira/Xray

## Requisitos Previos
- xray-connector ejecutándose
- Jira issue creado o identificado
- Test class abierta en editor

## Pasos

### Paso 1: Obtener Jira ID
```
¿Tienes Jira issue ID? (ej: PROJ-123)
Si no, ¿quieres crear uno?
```

### Paso 2: Generar template test
```java
@DisplayName("[JIRA-ID] descripción clara")
@TestKey("JIRA-ID")
@Test
void descriptiveTestName() {
    // Arrange
    
    // Act
    
    // Assert
}
```

### Paso 3: Pedir descripción
```
¿Qué debe validar este test?
(Copilot genera Given-When-Then)
```

### Paso 4: Completar implementación
Copilot genera test básico, usuario personaliza si necesario

### Paso 5: Validar
```bash
mvn -pl api-test test -Dtest=ClassNameTest#testMethodName
```

## Validación
✅ Test compila  
✅ Test ejecuta sin errores de sintaxis  
✅ Jira mapping confirmado  

## Troubleshooting

**Problema:** "TestKeyExtension no reconoce @TestKey"
- **Solución:** Verifica que extensión está en pom.xml

**Problema:** "xray-connector no conecta"
- **Solución:** Asegúrate de que está ejecutándose: `node build/index.js`
```

## Parte 5: Mejores Prácticas

### 1. Mantén Workflows Enfocados

❌ **Mal:** Workflow "Hacer Todo en el Proyecto"  
✅ **Bien:** Workflow "Crear Test Nueva" + "Ejecutar Tests" (separados)

Workflows con un objetivo claro son más reutilizables.

### 2. Documenta Pasos Claramente

❌ **Vago:**
```
Paso 1: Hacer lo que sea necesario
Paso 2: Validar
```

✅ **Claro:**
```
Paso 1: Ejecutar `mvn clean test -Dgroups=smoke`
Paso 2: Verificar que BUILD SUCCESS aparezca
Paso 3: Confirmar cero tests en error
```

### 3. Incluye Troubleshooting

Anticipa errores comunes. Los workflows serán ejecutados por otros.

### 4. Versiona Workflows

Cuando cambie convención, actualiza workflow:

```markdown
# Changelog
- v2.0 (Ene 2026): Agrega @TestKey mapping con xray
- v1.0 (Dic 2025): Versión inicial sin Jira
```

### 5. Pide Feedback

Después de usar workflow:
```
¿Faltó algo? ¿Pasos confusos? ¿Sugerencias?
→ Actualiza el workflow
```

## Parte 6: Automatización Avanzada

### Workflow Chaining

Workflows pueden encadenarse:

```
Workflow: "Release Completa"
  1. Ejecutar "Sincronizar Rama"
  2. Ejecutar "Ejecutar Todos los Tests"
  3. Ejecutar "Actualizar Versionado"
  4. Ejecutar "Crear Pull Request a Main"
  5. Pedir aprobación manual
```

### Workflows Condicionales

```markdown
# Workflow: Deploy Seguro

## Paso 1: Ejecutar tests
Si alguno falla → Pausar y reportar
Si todos pasan → Continuar

## Paso 2: Verificar seguridad
Ejecutar linter de seguridad
Si vulnerabilidades → Pausar
Si limpios → Continuar

## Paso 3: Deployment
[Solo si pasos anteriores pasan]
```

### Workflows con Parámetros

```
/crear-test-class-nueva --package=com.features --feature=login

Copilot rellena valores en template automáticamente
```

## Conclusión

Los workflows transforman procedimientos manuales repetitivos en operaciones fiables y documentadas. Tu equipo será más consistente, más rápido y cometerá menos errores.

**Principios clave:**
1. Documenta procedimientos que repetís frecuentemente
2. Mantén pasos claros y validaciones explícitas
3. Incluye troubleshooting
4. Versiona y actualiza según cambios del proyecto
5. Haz que toda el equipo los conozca

---

**Capítulo anterior:** [FAQ](faq.md)  
**Volver a:** [Índice](index.md)

**Última actualización:** Enero 2026
