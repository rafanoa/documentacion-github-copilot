# Guía Rápida de Instalación y Deployment

## 🚀 Instalación Local (5 minutos)

```bash
# 1. Navega a la carpeta
cd Documentacion-GitHub-Copilot

# 2. Instala dependencias (primera vez)
pip install -r requirements.txt

# 3. Sirve localmente
mkdocs serve

# 4. Abre en navegador
# http://localhost:8000
```

## 📦 Compilar para Producción

```bash
mkdocs build
```

Genera carpeta `site/` con archivos HTML listos para hospedar.

## 🌐 Publicar en GitHub Pages (Opción Recomendada)

### Paso 1: Preparar repositorio

```bash
# Si no está en git
git init
git add .
git commit -m "Initial commit: Copilot documentation"
```

### Paso 2: Crear repo en GitHub

1. Ve a github.com y crea nuevo repo
2. Nombra: `copilot-docs` (o similar)
3. Copia URL del repo

### Paso 3: Empujar código

```bash
# Añade origin
git remote add origin https://github.com/tu-usuario/copilot-docs.git

# Rama principal
git branch -M main
git push -u origin main
```

### Paso 4: Habilitar GitHub Pages

1. Ve a Settings > Pages
2. Source: Deploy from a branch
3. Branch: main
4. Folder: /docs (o crea rama gh-pages)
5. Save

### Paso 5 (Opcional): Automatizar con GitHub Actions

Crea `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - uses: actions/setup-python@v4
        with:
          python-version: '3.11'
      
      - run: pip install -r requirements.txt
      
      - run: mkdocs build
      
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
```

Resultado: Tu documentación en `https://tu-usuario.github.io/copilot-docs/`

---

## 🚀 Publicar en Netlify (Aún Más Fácil)

1. Ve a netlify.com
2. Clic en "New site from Git"
3. Conecta GitHub
4. Selecciona repo `copilot-docs`
5. Build command: `mkdocs build`
6. Publish directory: `site`
7. Deploy

**¡Listo!** Tu sitio está publicado.

---

## 📁 Estructura para Enterprise (Compartir con Empresa)

### Opción A: SharePoint/OneDrive

```bash
# 1. Compila
mkdocs build

# 2. Comprime site/
zip -r copilot-docs-site.zip site/

# 3. Sube a SharePoint
# 4. Comparte link con equipo
```

### Opción B: Servidor interno

```bash
# 1. Compila
mkdocs build

# 2. Copia site/ a servidor
scp -r site/ usuario@servidor:/var/www/docs/

# 3. Configura nginx (ver README principal)
```

### Opción C: Confluence

```bash
# 1. Compila a HTML
mkdocs build

# 2. Crea página en Confluence
# 3. Importa HTML o enlaza a carpeta compartida
```

---

## 🔄 Actualizar Documentación

```bash
# 1. Edita archivos en docs/

# 2. Preview
mkdocs serve

# 3. Cuando esté listo
git add .
git commit -m "Update docs: [descripción]"
git push

# Si usas GitHub Pages: se publica automáticamente
```

---

## ✅ Checklist Publicación

- [ ] Instalé `pip install -r requirements.txt`
- [ ] Ejecuté `mkdocs build` sin errores
- [ ] Creé repo en GitHub (o platforma elegida)
- [ ] Empujé código con `git push`
- [ ] Habilitación Pages/Netlify/otra plataforma
- [ ] Probé URL final
- [ ] Compartí URL con equipo

---

## 🆘 Troubleshooting

| Problema | Solución |
|----------|----------|
| "mkdocs not found" | `pip install mkdocs mkdocs-material` |
| Puerto 8000 ocupado | `mkdocs serve -a localhost:8001` |
| Cambios no visibles | Limpia: `rm -rf site/` y `mkdocs build` |
| GitHub Pages no actualiza | Espera 1-2 min o fuerza recarga (Ctrl+Shift+R) |
| Errores de markdown | Valida en archivos: `mkdocs build` te dice línea exacta |

---

**Próximos pasos:**
- Lee el [README principal](README.md) para opciones avanzadas
- Consulta [Documentación MkDocs](https://www.mkdocs.org/) para customización
- Añade más capítulos editando archivos en `docs/`

