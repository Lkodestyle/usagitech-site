# Usagitech - Website Corporativo IT

Website SPA profesional para consultora IT. HTML, CSS y JavaScript vanilla - simple, rápido y fácil de hostear.

## 📁 Estructura

```
website/
├── index.html          # Página principal (SPA)
├── css/
│   └── styles.css      # Estilos completos
├── js/
│   └── app.js          # Funcionalidad JS
└── assets/             # Imágenes y recursos (agregar)
```

## 🚀 Deployment

### Opción 1: S3 + CloudFront (Recomendado)

```bash
# 1. Crear bucket S3
aws s3 mb s3://usagitech-site --region us-east-1

# 2. Habilitar hosting estático
aws s3 website s3://usagitech-site \
  --index-document index.html \
  --error-document index.html

# 3. Subir archivos
aws s3 sync . s3://usagitech-site \
  --exclude ".git/*" \
  --exclude "README.md" \
  --cache-control "max-age=31536000" \
  --content-type "text/html" \
  --exclude "*" --include "*.html"

aws s3 sync . s3://usagitech-site \
  --exclude ".git/*" \
  --exclude "README.md" \
  --cache-control "max-age=31536000"

# 4. Configurar CloudFront (opcional pero recomendado para HTTPS y cache)
# Crear distribución apuntando al bucket S3
```

### Opción 2: GitHub Pages (Gratis)

1. Crear repositorio en GitHub
2. Subir archivos
3. Ir a Settings → Pages → Source: main branch
4. Listo, disponible en `https://usuario.github.io/repo`

### Opción 3: Vercel / Netlify (Gratis)

1. Conectar repositorio
2. Deploy automático
3. Dominio personalizado gratis

## ⚙️ Personalización

### Cambiar nombre de empresa

Buscar y reemplazar en `index.html`:
- `Usagitech` → Tu nombre de empresa
- `usagitech.com` → Tu dominio
- Actualizar meta tags (title, description, og:*)

### Cambiar colores

En `css/styles.css`, modificar variables CSS:

```css
:root {
    --color-primary: #10b981;        /* Verde principal */
    --color-accent: #06b6d4;         /* Cyan de acento */
    --color-bg: #0a0a0b;             /* Fondo oscuro */
    /* ... más variables */
}
```

### Cambiar fundadores

En `index.html`, buscar la sección `.about__founders` y modificar:
- Iniciales en `.founder-card__avatar`
- Nombres, roles y bios

### Agregar/modificar servicios

1. En la sección `#servicios`, duplicar o modificar `.service-card`
2. Crear/modificar modal correspondiente `#modal-[servicio]`

### Configurar formulario de contacto

El formulario actual simula el envío. Para producción:

**Opción A: Formspree (fácil)**
```html
<form action="https://formspree.io/f/TU_ID" method="POST">
```

**Opción B: Lambda + SES (tu stack)**
```javascript
// En app.js, descomentar y modificar el fetch
const response = await fetch('https://tu-api.com/contact', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(data)
});
```

### Agregar Analytics

Antes de `</head>` en `index.html`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXX');
</script>
```

## 📱 Responsive

El sitio es completamente responsive:
- Desktop: 1024px+
- Tablet: 768px - 1024px
- Mobile: < 768px

## 🔧 Tecnologías

- HTML5 semántico
- CSS3 (variables, flexbox, grid, animations)
- JavaScript ES6+ (vanilla)
- Fonts: Plus Jakarta Sans, JetBrains Mono (Google Fonts)
- Icons: SVG inline

## 📝 SEO

Ya incluido:
- Meta tags (title, description, keywords)
- Open Graph tags
- Estructura de headings correcta (H1 > H2 > H3)
- URLs semánticas (navegación por hash)
- HTML semántico

Para mejorar:
- Agregar sitemap.xml
- Agregar robots.txt
- Configurar Google Search Console
- Agregar schema.org markup (ya parcialmente incluido)

## 🎨 Secciones

1. **Hero** - Headline principal + código animado
2. **Value Props** - 3 propuestas de valor
3. **Servicios** - 5 servicios con modales de detalle
4. **Stats** - Métricas animadas
5. **Tech Stack** - Tecnologías organizadas por categoría
6. **Nosotros** - Historia + fundadores
7. **Proceso** - Timeline de 4 fases
8. **Casos de Éxito** - 3 casos con métricas
9. **CTA** - Llamada a la acción
10. **Contacto** - Formulario + datos
11. **FAQ** - Preguntas frecuentes (acordeón)
12. **Footer** - Links + copyright

## 📄 Licencia

Libre para uso comercial. Personalizar y usar como quieras.

---

**Desarrollado para Usagitech** | 2025
