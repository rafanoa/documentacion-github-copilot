# Capítulo 1: Comenzar — Instalación y Configuración

## Introducción

Este capítulo te guiará paso a paso en la instalación de GitHub Copilot y la configuración inicial. No te llevaremos por caminos complejos; nos enfocamos en que tengas Copilot funcionando correctamente en menos de 5 minutos.

Al final de este capítulo:
- ✅ Tendrás Copilot instalado en tu VS Code
- ✅ Tu cuenta estará autenticada correctamente
- ✅ Conocerás los atajos esenciales
- ✅ Sabrás dónde acceder a settings si necesitas ajustes

## Requisitos previos

Antes de comenzar, asegúrate de tener:

**Software**
- VS Code versión 1.86 o superior (o cualquier IDE compatible: Visual Studio, JetBrains, etc.)
- Una conexión estable a Internet

**Cuenta y suscripción**
- Una cuenta activa de GitHub
- Una suscripción a GitHub Copilot (Individual, Pro o Business) o una prueba gratuita activa

**Nota:** Actualmente, GitHub ofrece 2 meses de prueba gratuita a nuevos usuarios. Después, requiere suscripción de pago.

Si no tienes suscripción, puedes obtenerla en [github.com/copilot](https://github.com/copilot).

## Instalación en VS Code

### Paso 1: Instalar la extensión de GitHub Copilot

1. Abre **Visual Studio Code**
2. En el lado izquierdo, haz clic en el icono **Extensions** (parece un cuadrado dividido en 4)
   - Atajo alternativo: `Ctrl+Shift+X`
3. En la barra de búsqueda en la parte superior, escribe `GitHub Copilot`
4. En los resultados, busca la extensión oficial de **GitHub** (debe tener el logo de GitHub)
5. Haz clic en el botón verde **Install**
6. Espera a que se complete la instalación (toma unos segundos)

**Verificación:** Después de instalar, deberías ver un botón **Sign in to use GitHub Copilot** o una notificación similar.

### Paso 2: Autenticar tu cuenta de GitHub

1. Cuando se complete la instalación, verás un banner notificándote que necesitas iniciar sesión
2. Haz clic en **Sign in to use GitHub Copilot**
   - Alternativa: Presiona `Ctrl+Shift+P`, busca `Copilot: Sign in` y presiona Enter
3. Se abrirá una ventana del navegador pidiéndote que permitas acceso
4. Inicia sesión con tu cuenta de GitHub si no lo has hecho
5. Revisa los permisos que solicita (principalmente acceso a tu cuenta) y haz clic en **Authorize**
6. El navegador mostrará un mensaje confirmando el acceso
7. Vuelve a VS Code - ¡Copilot está listo para usar!

**Verificación:** En la barra de estado de VS Code (abajo), deberías ver el logo de Copilot en púrpura. Esto indica que está conectado y disponible.

### Paso 3: Configuración recomendada inicial

Antes de usar Copilot, aplicaremos una configuración básica para máxima experiencia:

1. Abre **Settings** en VS Code
   - Atajo: `Ctrl+,` (Ctrl + coma)
   - O: File > Preferences > Settings

2. En la barra de búsqueda de Settings, escribe `copilot`

3. Busca estas opciones y asegúrate de que estén configuradas:

**Editor: Inline Suggest** → Debe estar **ON** (habilitado)
Permite que Copilot muestre sugerencias mientras escribes.

**Copilot: Autocomplete** → Debe estar **ON**
Habilita las sugerencias automáticas mientras escribes.

Esas son las configuraciones esenciales. Puedes dejar el resto con valores por defecto por ahora.

## Primeros pasos: Atajos esenciales

Memoriza estos tres atajos; los usarás constantemente:

| Atajo | Qué hace | Cuándo usarlo |
|-------|----------|---------------|
| `Ctrl+I` | Abre inline chat en el editor | Cuando quieres cambios rápidos en el código actual |
| `Ctrl+K` | Abre chat lateral para conversaciones amplias | Para debates arquitectónicos o aprendizaje |
| `Escape` | Cierra el chat sin aplicar cambios | Para cancelar sin aceptar sugerencias |

**Nota:** Tab/Enter para aceptar sugerencias varía según tu configuración de VS Code.

## Tu primer uso: "Hola, Copilot"

Hagamos una pequeña prueba para confirmar que todo funciona:

1. Abre o crea un archivo de código simple (ej: `test.js`, `hello.py`, `main.ts`)
2. Escribe un comentario describiendo algo simple:
   ```javascript
   // función que suma dos números
   ```
3. Presiona `Ctrl+I` para abrir inline chat
4. En la ventana que aparece, escribe:
   ```
   generar esta función
   ```
5. Presiona Enter o click en un botón para ejecutar

Copilot debería sugerir una función simple. Puedes aceptarla con Tab o rechazarla con Escape.

Si funciona, ¡congratulaciones! Tienes Copilot operativo.

## Solución de problemas comunes

### Problema: "Copilot extension not found" o no aparece en extensiones

**Solución:**
- Asegúrate de estar usando VS Code versión 1.86 o superior: Help > About
- Si tu versión es más antigua, actualiza VS Code
- Reinicia VS Code

### Problema: Se pide iniciar sesión repetidamente

**Solución:**
1. Abre Command Palette: `Ctrl+Shift+P`
2. Busca y ejecuta: `Copilot: Sign Out`
3. Espera 10 segundos
4. Ejecuta: `Copilot: Sign In`
5. Completa el proceso de autenticación nuevamente

### Problema: No aparecen sugerencias al escribir

**Solución:**
1. Verifica que Copilot esté habilitado: Settings > busca "Editor Inline Suggest"
2. Asegúrate de que esté en **ON**
3. Verifica tu conexión a Internet
4. Reinicia VS Code
5. Prueba presionando `Ctrl+I` manualmente

### Problema: "Copilot is not available for this user"

**Solución:**
- Tu suscripción de Copilot ha expirado o no está activa
- Verifica en [github.com/account/billing/summary](https://github.com/account/billing/summary) si tu suscripción está activa
- Si tienes prueba gratuita, verifica que no haya expirado

### Problema: La extensión se instala pero no funciona

**Solución nuclear (reinicia todo):**
1. Desinstala completamente la extensión GitHub Copilot
2. Cierra VS Code
3. Abre VS Code nuevamente
4. Reinstala la extensión desde el marketplace
5. Vuelve a hacer Sign in

## Modelos de suscripción

Comprende qué plan tienes y sus limitaciones:

**Prueba gratuita**
- Duración: 2 meses para nuevos usuarios
- Costo después: Requiere suscripción de pago
- Mejora automática: No

**Copilot Individual**
- Costo: $10/mes o $100/año
- Límites: Generosos (cientos de completions diarias)
- Mejor para: Desarrolladores independientes

**Copilot Pro**
- Costo: $20/mes
- Límites: Más altos que Individual
- Acceso a modelo GPT-4 (más potente)
- Mejor para: Profesionales que usan Copilot intensivamente

**Copilot for Business**
- Administrado por: Tu organización
- Costo: Por suscripción de negocio
- Control: Políticas empresariales
- Mejor para: Equipos corporativos

## Consideraciones de privacidad y datos

Es importante que entiendas qué pasa con tu código:

**Qué se envía a GitHub:**
Para poder generar sugerencias, fragmentos de tu código se envían a servidores de GitHub para procesamiento.

**Qué NO se usa para entrenamiento:**
- Con Copilot for Business, tu código no se usa para entrenar modelos de GitHub
- Consulta la política de privacidad específica de tu plan en [github.com/copilot/privacy](https://github.com/copilot/privacy)

**Recomendación de seguridad:**
No compartas información sensible (credenciales, API keys, datos personales) en chats de Copilot. Trata a Copilot como si fuese un compañero de trabajo público.

## Configuración avanzada (opcional)

Si deseas ajustes más finos, Settings contiene muchas opciones:

**Para acceso rápido:**
- Abre Settings: `Ctrl+,`
- Busca "copilot"
- Ajusta según tus preferencias

Algunas opciones interesantes:
- `Inline Suggest Mode`: Cambia si las sugerencias aparecen inline o en un popup
- `Inline Suggest Count`: Número de sugerencias diferentes que propone
- `Inline Suggest Hide`: Ocultar sugerencias automáticas (solo mostrar cuando presionas Ctrl+I)

**Consejo:** Por ahora, mantén valores por defecto. Después de una semana de uso, ajusta según tus preferencias.

## Resumen de la instalación

✅ Instalaste la extensión GitHub Copilot  
✅ Autenticaste tu cuenta de GitHub  
✅ Configuraste los settings básicos  
✅ Probaste que funciona correctamente  
✅ Entiendes los atajos esenciales  

## Siguiente paso

Ahora que tienes Copilot operativo, estás listo para aprender a usarlo efectivamente. El siguiente capítulo, **[Inline Chat](inline-chat.md)**, te enseñará las 8 operaciones fundamentales que ejecutarás diariamente.

---

**Capítulo anterior:** [Introducción](index.md)  
**Capítulo siguiente:** [Inline Chat — Interacción Contextual](inline-chat.md)
