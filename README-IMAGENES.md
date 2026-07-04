# Clínica Dra. Ana Escapa — guía rápida

## 1. Fotos que faltan

La web está diseñada para que, en cuanto añadas estos archivos dentro de la carpeta
`images/`, aparezcan automáticamente (si no están, se ve un degradado verde elegante
en su lugar, así que la web nunca se ve "rota"):

| Archivo a crear                     | Dónde se usa                          | Tamaño recomendado |
|--------------------------------------|----------------------------------------|---------------------|
| `images/hero-clinica.jpg`            | Fondo lateral de la portada             | 1200x1600 px |
| `images/doctora-ana-escapa.jpg`      | Foto de la Dra. Ana Escapa (sección "Sobre la clínica") | 900x1100 px |
| `images/clinica-interior-1.jpg`      | Galería "Nuestro espacio" (foto grande) | 1200x900 px |
| `images/clinica-interior-2.jpg`      | Galería "Nuestro espacio"               | 800x800 px |
| `images/clinica-interior-3.jpg`      | Galería "Nuestro espacio"               | 800x800 px |
| `images/og-image.jpg`                | Vista previa al compartir en WhatsApp/redes | 1200x630 px |

**Sobre el logo:** ya está integrado en `images/logo-mark.svg` y `images/favicon.svg`,
reconstruido a partir de la imagen que enviaste (verde y forma exactos). Es una
recreación vectorial, no el archivo original — si en algún momento tienes el archivo
original del logo (PNG en alta resolución, AI, EPS o SVG), pásamelo y hago el cambio
para que sea pixel-perfecto.

Recomendación: usa fotos reales del interior de la clínica y una foto profesional
de tu madre. Para las fotos de tratamientos/pacientes de Instagram, mejor pedirle a
ella que elija cuáles autoriza a publicar en la web (hay una foto de paciente que se
identifica fácilmente en algunas imágenes de "antes/después", y es mejor confirmarlo
directamente con ella antes de publicarlas fuera de Instagram).

## 2. Dominio, hosting y Google

Ver [DOMINIO-Y-DESPLIEGUE.md](DOMINIO-Y-DESPLIEGUE.md) — guía paso a paso completa para
comprar el dominio, conectarlo a un hosting y vincularlo con Google Search Console /
Google Business Profile.

## 3. Formulario de contacto

El formulario usa **Netlify Forms** (incluido gratis con el hosting, hasta 100 envíos al
mes — no hace falta ninguna cuenta ni servicio externo). Solo falta un paso, que se
configura en el panel de Netlify, no en el código — ver el punto 6 de
[DOMINIO-Y-DESPLIEGUE.md](DOMINIO-Y-DESPLIEGUE.md).

## 4. Cómo ver la web

Simplemente abre `index.html` con doble clic, o usa un servidor local (`npx serve` o
la extensión "Live Server" si usas VS Code) para ver las animaciones exactamente como
se verán en producción.
