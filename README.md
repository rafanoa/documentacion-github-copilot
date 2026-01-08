# Documentación GitHub Copilot - Proyecto MkDocs

Este proyecto contiene documentación completa sobre GitHub Copilot con múltiples capítulos, ejemplos y mejores prácticas.

## Estructura del Proyecto

```
Documentacion-GitHub-Copilot/
├── mkdocs.yml           # Configuración de MkDocs
├── requirements.txt     # Dependencias Python
├── README.md            # Este archivo
├── docs/
│   ├── index.md                 # Página inicio
│   ├── getting-started.md        # Instalación y setup
│   ├── inline-chat.md            # Guía completa inline chat
│   ├── chat-lateral.md           # Chat lateral (Copilot Chat)
│   ├── mejores-practicas.md      # Estrategias avanzadas
│   └── faq.md                    # Preguntas frecuentes
└── site/                # Generado (sitio HTML)
```

## Instalación y Uso

### Requisitos previos

- Python 3.7+
- pip (gestor de paquetes Python)

### 1. Clonar o descargar el proyecto

```bash
cd Documentacion-GitHub-Copilot
```

### 2. Instalar dependencias

```bash
pip install -r requirements.txt
```

### 3. Servir localmente (desarrollo)

```bash
mkdocs serve
```

Luego abre en tu navegador: `http://localhost:8000`

El servidor recargará automáticamente cuando hagas cambios en los archivos.

### 4. Compilar para producción

```bash
mkdocs build
```

Esto genera la carpeta `site/` con todos los archivos HTML estáticos listos para hospedar.

## Opciones de Hosting/Compartición con tu Empresa

Aquí están todas las opciones para compartir esta documentación con tu empresa:

### 🌐 **Opción 1: Hosting Gratuito (Recomendado - Rápido)**

#### A. GitHub Pages (Gratuito, Integrado)

```bash
# 1. Crea un repo en GitHub
# 2. Empuja el código (incluyendo carpeta site/)
# 3. Ve a Settings > Pages
# 4. Selecciona "Deploy from a branch"
# 5. Rama: main, carpeta: /docs (si estás usando mkdocs)
# O usa carpeta /site después de hacer build

# Para automatizar con GitHub Actions:
```

Crea `.github/workflows/deploy.yml`:

```yaml
name: Deploy Documentation

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.11'
      - run: pip install -r requirements.txt
      - run: mkdocs build
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
```

**Resultado:** Tu documentación en `https://username.github.io/proyecto/`

#### B. Netlify (Gratuito)

1. Sube tu proyecto a GitHub
2. Conecta Netlify (netlify.com)
3. Selecciona el repo
4. Build command: `mkdocs build`
5. Publish directory: `site`
6. Deploy automático con cada push

**Resultado:** URL personalizada tipo `tu-docs.netlify.app`

#### C. Vercel (Gratuito)

Similar a Netlify:
1. Importa desde GitHub
2. Configure build: `mkdocs build`
3. Publish: `site`

**Resultado:** URL tipo `tu-docs.vercel.app`

---

### 🏢 **Opción 2: Hosting Empresarial (Privado)**

#### A. SharePoint/OneDrive (Empresarial Microsoft)

```bash
# 1. Compila: mkdocs build
# 2. Comprime carpeta site/
# 3. Sube a SharePoint
# 4. Comparte con equipo
```

**Ventajas:** Integrado en Microsoft 365, permisos granulares

#### B. Confluence (Si tu empresa usa)

```bash
# 1. Exporta markdown a HTML: mkdocs build
# 2. Importa a Confluence
# O crea página en Confluence y enlaza al HTML generado
```

#### C. Wiki Empresarial (GitLab, Gitea, etc.)

Si usas GitLab en la empresa:

1. Activa GitLab Pages en tu repo
2. Crea `.gitlab-ci.yml`:

```yaml
pages:
  stage: deploy
  script:
    - pip install -r requirements.txt
    - mkdocs build -d public
  artifacts:
    paths:
      - public
  only:
    - main
```

**Resultado:** Disponible en `https://gitlab.empresa.com/proyecto/`

---

### 🖥️ **Opción 3: Hosting Propio (Máximo Control)**

#### A. Servidor Apache/Nginx

```bash
# 1. Compila: mkdocs build
# 2. Sube carpeta site/ a tu servidor
# 3. Configura vhost en Apache/Nginx
```

Ejemplo Nginx:

```nginx
server {
    listen 80;
    server_name docs.empresa.com;
    
    root /var/www/copilot-docs/site;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

#### B. Docker

Crea `Dockerfile`:

```dockerfile
FROM python:3.11
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
RUN mkdocs build
EXPOSE 80
CMD ["python", "-m", "http.server", "80", "--directory", "site"]
```

```bash
docker build -t copilot-docs .
docker run -p 8000:80 copilot-docs
```

---

### 📱 **Opción 4: Soluciones SaaS Profesionales**

#### ReadTheDocs (Gratuito para open source, Pago para privado)

1. Ve a readthedocs.org
2. Conecta tu GitHub/GitLab
3. Importa proyecto
4. Construcción automática

**Ventajas:** Profesional, documentación versionada, búsqueda avanzada

#### GitBook (Pago)

1. Importa markdown
2. Editor visual
3. Hospedaje automático
4. Colaboración en tiempo real

**Costo:** Desde $0 (free tier) a empresarial

---

## Comparativa Rápida - Opciones para Empresa

| Opción | Setup | Costo | Privado | Colaboración | Recomendado |
|--------|-------|-------|---------|--------------|-------------|
| **GitHub Pages** | 5 min | Gratis | Con privacidad | Buena | ⭐⭐⭐⭐⭐ |
| **Netlify** | 5 min | Gratis | Con plan pago | Buena | ⭐⭐⭐⭐ |
| **Confluence** | 10 min | Incluido | Sí (empresarial) | Excelente | ⭐⭐⭐⭐ |
| **ReadTheDocs** | 5 min | Pago | Sí | Buena | ⭐⭐⭐⭐ |
| **GitBook** | 5 min | Pago | Sí | Excelente | ⭐⭐⭐⭐ |
| **Servidor propio** | 20 min | Variable | Sí | Manual | ⭐⭐⭐ |
| **SharePoint** | 10 min | Incluido | Sí | Excelente | ⭐⭐⭐⭐ |

---

## Mi Recomendación para tu Empresa

### Pequeña empresa (<50 personas)
→ **GitHub Pages** (Gratuito, profesional)

### Empresa mediana
→ **Confluence** o **ReadTheDocs Pro** (Controlado, seguro)

### Empresa grande
→ **Servidor propio + Docker** o **Confluence** (Máximo control)

### Enfoque ágil/startup
→ **GitBook** (Mejor UX, colaboración en vivo)

---

## Expandir la Documentación

Para añadir más documentos:

1. Crea archivo `.md` en la carpeta `docs/`
2. Añade entrada al `mkdocs.yml` bajo `nav:`
3. Ejecuta `mkdocs serve` para preview
4. Compila con `mkdocs build`

Ejemplo:

```yaml
nav:
  - Inicio: index.md
  - Nuevas guías:
      - Mi nueva guía: mi-nueva-guia.md
```

---

## Problemas Comunes

### "mkdocs: command not found"

```bash
# Instala mkdocs globalmente
pip install mkdocs mkdocs-material
```

### Puerto 8000 en uso

```bash
# Usa otro puerto
mkdocs serve -a localhost:8001
```

### Los cambios no se reflejan

```bash
# Limpia caché
rm -rf site/
mkdocs build
mkdocs serve
```

---

## Recursos Útiles

- [Documentación oficial MkDocs](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

---

**¿Necesitas ayuda?** Abre un issue o consulta los documentos en la carpeta `docs/`.

**Última actualización:** Enero 2026
