# Rumbo lento

Planificador web de escapadas desde Sant Celoni para enero y febrero de 2027. El sitio se publica como contenido estático en GitHub Pages y consulta el catálogo del workflow de n8n.

## Publicar en GitHub Pages

1. Crea un repositorio llamado `rumbo-lento` y sube estos archivos a la rama `main`.
2. En **Settings → Pages**, elige **GitHub Actions** como origen de publicación.
3. El workflow `.github/workflows/pages.yml` publica `index.html` automáticamente al subir cambios a `main`.
4. La dirección tendrá el formato `https://<usuario>.github.io/rumbo-lento/`.

El repositorio debe ser público para la configuración gratuita típica de GitHub Pages. El sitio publicado será público en cualquier caso.

## API de n8n

El navegador consulta:

`https://lsanhueza.oph.st/webhook/rumbo-lento/v1`

Parámetros disponibles: `travelers` (1–9), `budget` (euros por persona) e `interest` (`all`, `shopping`, `culture`, `nature` o `easy`). La API es pública y de solo lectura; no recibe datos personales.

## Precios y base de datos

Los importes del catálogo son demostrativos y no son tarifas verificadas. Los eventos de 2027 también están pendientes de confirmación. Esta versión no necesita PostgreSQL: no guarda perfiles, reservas ni precios consultados. Si se incorporan fuentes tarifarias reales, se podrá añadir una tabla propia para caché, fecha de consulta y fuente, sin modificar las tablas internas de n8n.
