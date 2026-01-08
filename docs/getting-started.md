# Getting Started - Instalación y Configuración

## Requisitos previos

Para usar GitHub Copilot necesitas:

- **VS Code** versión 1.86 o superior (o compatible IDE)
- **Suscripción a GitHub Copilot** (versión de pago o prueba gratuita)
- **Conexión a Internet** para conectar con los servidores de Copilot
- **Cuenta de GitHub** autenticada

## Instalación en VS Code

### Paso 1: Instalar la extensión

1. Abre VS Code
2. Ve a la pestaña **Extensions** (Ctrl+Shift+X)
3. Busca "GitHub Copilot"
4. Haz clic en **Install** en la extensión oficial de GitHub

### Paso 2: Autenticar tu cuenta

1. Después de instalar, verás una notificación para "Sign in to use GitHub Copilot"
2. Haz clic en **Sign in** (o Ctrl+Shift+P y busca "Copilot: Sign in")
3. Se abrirá tu navegador para autenticarte con GitHub
4. Permite el acceso
5. Vuelve a VS Code - ¡Listo!

### Paso 3: Configuración recomendada

Abre VS Code Settings (Ctrl+,) y busca "Copilot" para personalizar:

- **Inline Suggest Enabled**: Activar sugerencias inline
- **Inline Suggest Mode**: Establece a "inline" o "block"
- **Accept On Commit Character**: Si quieres aceptar con Enter

## Primeros pasos

Una vez instalado, puedes empezar inmediatamente:

- **Ctrl+I**: Abre inline chat
- **Ctrl+K**: Abre chat lateral
- **Ctrl+Shift+A**: Abre Copilot en VS Code

## Limitaciones y cuotas

- **Plan Copilot Individual**: Acceso ilimitado
- **Plan Copilot Pro**: Mayores límites de requests
- **Prueba gratuita**: 2 meses para nuevos usuarios

## Troubleshooting

### "Copilot not available"
Verifica que tu suscripción esté activa en tu cuenta de GitHub.

### Sin sugerencias
Asegúrate de que "Inline Suggest Enabled" está activado en settings.

### Problemas de autenticación
Logout y login nuevamente:
```
Ctrl+Shift+P > Copilot: Sign Out
Ctrl+Shift+P > Copilot: Sign In
```

---

**Siguiente paso:** Lee [Inline Chat](inline-chat.md) para aprender a usar la herramienta.
