# Instructions — Personalización de Copilot

## Introducción

Las **instructions** (instrucciones) son la forma más poderosa de personalizar el comportamiento de GitHub Copilot. Permiten definir patrones, preferencias y restricciones globales que Copilot respetará en todas tus conversaciones, sin necesidad de repetirlas cada vez.

Es como tener un "sistema de instrucciones" que le dices una sola vez a Copilot y él lo recuerda indefinidamente.

## ¿Qué son las Instructions?

Las instructions son directivas persistentes que defines para que Copilot:

- Siga convenciones específicas de tu proyecto
- Respete restricciones técnicas (p.ej., "sin librerías externas")
- Adopte un estilo de escritura o comunicación
- Genere código en ciertos patrones
- Excluya temas o tecnologías
- Siga estándares empresariales

Una vez defines las instructions, Copilot las aplica automáticamente en todos los chats hasta que las cambies.

## Acceso a Instructions: La Rueda Dentada

### Ubicación en VS Code

1. Abre el **Chat de Copilot** (Ctrl+K)
2. Busca el **icono de rueda dentada (⚙️)** en la esquina superior derecha del panel de chat
3. Haz clic en **"Settings"** o **"Copilot Settings"**

Alternativamente:
- Ve a **VS Code Settings** (Ctrl+,)
- Busca **"Copilot"**
- Encuentra la sección **"Instructions"** o **"Chat Instructions"**

### Interfaz de Settings

En settings encontrarás:
- **Instructions**: Campo de texto donde defines tus instrucciones globales
- **Predefined Instructions**: Instrucciones predefinidas que puedes activar
- **Clear Instructions**: Opción para eliminar instrucciones actuales

## Crear una New Chat Instruction

### Opción 1: Desde la rueda dentada (UI)

1. Abre Copilot Chat (Ctrl+K)
2. Haz clic en ⚙️ (Settings)
3. Busca la sección "Instructions" o "Custom Instructions"
4. Haz clic en "New Instruction" o "+ Add"
5. Define tu instrucción
6. Guarda

### Opción 2: Editar directamente en settings.json

Ve a **File > Preferences > Settings > Copilot** o edita `.vscode/settings.json`:

```json
{
  "github.copilot.chat.instructions": [
    "Siempre responde en español",
    "Usa solo JavaScript ES6+, no TypeScript",
    "Aplica patrón MVC en todas las sugerencias"
  ]
}
```

## Estructura y Sintaxis de Instructions

Una instruction efectiva tiene esta estructura:

```
[Prefijo] [Acción] [Detalles/Requisitos]
```

### Ejemplos de buenos formatos

**Restricciones:**
```
No uses bibliotecas externas, solo APIs nativas de JavaScript
```

**Preferencias de estilo:**
```
Genera código con comentarios explicativos en español
```

**Patrones específicos:**
```
Sigue el patrón Singleton para clases y componentes
```

**Contexto:**
```
Estoy trabajando en un proyecto Node.js con Express y MongoDB
Respeta esa stack en todas tus sugerencias
```

**Exclusiones:**
```
Nunca sugiera usar jQuery o librerías depreciadas
```

## Ejemplos Reales de Instructions

### Para proyecto Frontend React

```
Contexto: Proyecto React 18 con TypeScript y Tailwind CSS

Preferencias:
- Usa componentes funcionales con hooks
- Sigue convención de nombres: PascalCase para componentes
- Usa Tailwind CSS para styling, nunca CSS modules
- Asume que useContext y useReducer están disponibles
- Genera componentes sin PropTypes, usa TypeScript para tipos

Restricciones:
- No uses clases (solo functional components)
- No uses referencias a React.FC, es depreciado
- No sugiera Next.js features fuera de contexto

Formato:
- Añade comentarios explicativos
- Incluye ejemplos de uso cuando sea pertinente
```

### Para proyecto Backend API

```
Contexto: Node.js/Express API con MongoDB

Reglas:
- Usa async/await, nunca callbacks
- Estructura de carpetas: routes/ | controllers/ | models/ | middleware/
- Manejo de errores: Express middleware de errores centralizado
- Validación: Usa Joi para validación de inputs

Prohibido:
- No uses ORM (Mongoose, Sequelize), solo queries raw
- No sugiera arquitecturas serverless
- No uses tipos globales, importa siempre explícitamente

Código:
- Incluye error handling
- Comenta funciones complejas
```

### Para documentación técnica

```
Eres experto en documentación técnica clara y accesible

Estilo:
- Lenguaje simple, evita jerga innecesaria
- Estructura: Intro → Concepto → Ejemplo → Caso de uso → Tips
- Usa markdown con títulos jerárquicos claros
- Incluye siempre ejemplos de código funcionando

Audiencia:
- Desarrolladores junior (explica desde lo básico)
- Dale contexto antes de detalles técnicos

Restricciones:
- No hagas textos mayores de 500 palabras por sección
- Si es complejo, divide en subsecciones
```

## Mejores Prácticas

### 1. Sé específico, no genérico

❌ **Malo:**
```
Genera buen código
```

✅ **Bueno:**
```
Genera código JavaScript limpio con ES6+ features,
sigue convención camelCase, incluye manejo de errores
y comenta cada función con propósito y parámetros
```

### 2. Estructura jerárquica

Organiza tus instructions en niveles:

```
1. CONTEXTO
   - Proyecto: [Nombre]
   - Stack: [Tech stack]
   - Versiones: [Versiones específicas]

2. PREFERENCIAS
   - Estilo: [Convenciones]
   - Patrones: [Patrones de diseño]
   - Lenguaje: [Español/Inglés]

3. RESTRICCIONES
   - Prohibido: [Lo que no se debe usar]
   - Evitar: [Lo que se puede evitar]

4. FORMATO/SALIDA
   - Comentarios: [Cómo]
   - Documentación: [Tipo]
   - Ejemplos: [Cuándo]
```

### 3. Usa negaciones explícitas

```
NO hagas: [cosa]
Nunca sugiera: [cosa]
Evita: [cosa]
```

Copilot entiende mejor lo que NO debe hacer.

### 4. Limita a lo esencial

Si tienes +10 instructions, probablemente hay redundancia. Consolida:

```
❌ Instrucción 1: No uses var
❌ Instrucción 2: Usa const y let
→ ✅ Consolidada: Usa const y let, nunca var
```

### 5. Agrupa por tema

```
// ESTILO DE CÓDIGO
Usa camelCase para funciones y propiedades
Usa UPPERCASE para constantes globales

// VALIDACIÓN
Valida siempre inputs de usuario
Maneja nulos/undefined explícitamente

// RENDIMIENTO
Evita cálculos repetidos en loops
Usa memoización para funciones complejas
```

## Trucos Avanzados

### 1. Instructions dinámicas por contexto

En lugar de una mega-instruction única, crea varias y habilita según contexto:

```json
{
  "copilot.instructions.frontend": "...",
  "copilot.instructions.backend": "...",
  "copilot.instructions.docs": "..."
}
```

Luego activa la pertinente cuando trabajas en esa área.

### 2. Reference instructions desde archivos

Algunos IDEs permiten referenciar archivos `.md` con instructions:

```json
{
  "github.copilot.chat.instructions": "@docs/copilot-instructions.md"
}
```

Esto centraliza instructions en tu repo (compartible con equipo).

### 3. Combina instructions con inline comments

Global instruction:
```
Usa async/await siempre
```

En código:
```javascript
// Copilot: esta función requiere manejo de timeout especial
async function fetchWithTimeout(url, timeout = 5000) {
  // Copilot generará respetando la instruction global
  // pero considerando el contexto local
}
```

### 4. Instructions para patrones de proyecto

```
Convención de carpetas:
src/
  ├── components/  (React components)
  ├── hooks/       (Custom hooks)
  ├── utils/       (Funciones auxiliares)
  ├── types/       (TypeScript types)
  ├── styles/      (CSS/Tailwind)

Cuando sugieras código, respeta esta estructura
```

### 5. Validación de instructions

Después de cambiar instructions, prueba con un caso pequeño:

```
/generate una función de validación de email
```

Si Copilot respeta tus instrucciones, está funcionando. Si no, refina la instrucción.

## Casos de Uso Reales

### Onboarding de equipo

Instructions centralizadas para nuevos developers:

```
Bienvenido al proyecto. Copilot seguirá estas reglas:

1. Stack: Node.js 18 + Express + MongoDB
2. Archivos: TypeScript, no JavaScript
3. Testing: Jest con convención [name].test.ts
4. Estilo: Prettier + ESLint config del proyecto
5. Commits: Sigue conventional commits

Nunca desvíes de estas normas sin consultar con el lead.
```

### Mantenimiento de legacy

```
Este es código heredado de 2019. Copilot debe:
- No refactorizar masivamente (rompe compatibilidad)
- Documentar cambios
- Respetar convenciones antiguas del proyecto
- Usar solo librerías que ya están en package.json

Objetivo: mejoras incrementales, no rewrite.
```

### Documentación multiidioma

```
Generas documentación en español para audiencia hispana.

Convenciones:
- Usa "tú" (no "usted")
- Mantén párrafos cortos
- Incluye ejemplos en contexto local
- Traduce API docs, no hagas transcripción literal
```

## Limitaciones y Consideraciones

- **No es garantía:** Copilot intenta seguir instructions pero puede no hacerlo al 100% en casos complejos. Siempre revisa.
- **Contexto local prevalece:** Un comentario inline bien específico puede superar una instruction global.
- **Complejidad:** Demasiadas instructions pueden confundir a Copilot. Menos es más.
- **Versión de Copilot:** Las instructions funcionan mejor en versiones recientes. Asegúrate de tener la última.

## Checklist: Instructions Efectivas

- [ ] ¿Son claras y sin ambigüedades?
- [ ] ¿Evitan contradicciones internas?
- [ ] ¿Son específicas a tu proyecto (no genéricas)?
- [ ] ¿Las probaste con un caso pequeño?
- [ ] ¿Se adaptan bien al cambiar contexto?
- [ ] ¿Son mantenibles (no requieren rewrite cada mes)?
- [ ] ¿Tu equipo las conoce y entiende?

## Tips Finales

1. **Documenta tus instructions:** Guarda una copia en `docs/copilot-instructions.md` de tu repo. Así el equipo las conoce.

2. **Itera:** Las primeras instructions rara vez son perfectas. Refina basándote en resultados.

3. **Comparte:** Si descubres una instruction que funciona bien, comparte con el equipo.

4. **Revisa periódicamente:** Cada trimestre, evalúa si las instructions siguen siendo relevantes.

5. **Usa como especificación:** Trata instructions como un "specification sheet" para Copilot. Cuanto más clara, mejor funciona.

---

**Última actualización:** Enero 2026

**Nota:** Las instructions son una feature en evolución. Comprueba la documentación oficial de GitHub Copilot para cambios recientes.
