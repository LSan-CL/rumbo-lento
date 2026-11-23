# Rumbo lento

Planificador web de escapadas desde Sant Celoni para enero y febrero de 2027. El sitio se publica como contenido estático en GitHub Pages y consulta el catálogo de muestra del workflow de n8n.

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

## Fichas e itinerario

Cada destino tiene una ficha local con actividades, fotos, recomendaciones de paseo por mañana/tarde/noche, ideas de compras locales, gastronomía y costes pendientes de confirmar. Se pueden añadir actividades a **Mi paseo**, asignarles fecha, quitarlas y consultar un total conocido para el grupo. Los destinos internacionales con tarifa incompleta permanecen visibles aunque se use el filtro de presupuesto; aparecen como **Por cotizar** y no se incluyen en el total.

En Montserrat se puede añadir **Trans Montserrat** o **Tot Montserrat** al itinerario, pero no ambos el mismo día. El sistema incorpora su tarifa “desde”, no vuelve a sumar las actividades que incluye y deja el trayecto Sant Celoni–Barcelona como pendiente de confirmar. El servicio de Santa Cova está sujeto a operativa.

Se añadieron Perpiñán, Collioure, Montpellier, Carcasona y Lyon. La guía recomienda al menos una noche para las rutas más largas: los tiempos indicados son desde Barcelona Sants y no incluyen Sant Celoni–Barcelona ni posibles esperas de transbordo. La búsqueda consultada el 23/11/2026 mostraba mínimos de 1 h 26 min / 35 € por trayecto para Perpiñán, 3 h 17 min / 39 € para Montpellier, 3 h 13 min para Carcasona (con conexión) y 5 h 14 min / 59 € para Lyon. Son precios de selección de fechas actuales, no tarifas garantizadas para el viaje de 2027. Collioure requiere enlazar con el TER desde Perpiñán. El museo de arte de Collioure figura cerrado hasta 2028 según su oficina de turismo.

El itinerario se guarda en el almacenamiento local del navegador y no se envía a n8n. Las fechas del 6 al 8 de febrero de 2027 están bloqueadas. Si se cambia de dispositivo o se borran los datos del navegador, el plan no se conserva.

## Precios y base de datos

Los precios deben confirmarse para las fechas del viaje (enero–febrero de 2027); las tarifas publicadas pueden cambiar:

- **Montserrat**, consultado el 23/11/2026 en [Turistren/FGC](https://turistren.cat/es/trenes/cremallera-y-funiculares-de-montserrat/): Trans Montserrat desde 50 € y Tot Montserrat desde 71,50 € por persona. Son pases desde Barcelona; el trayecto desde Sant Celoni no está incluido. Consulta [disponibilidad y condiciones](https://www.cremallerademontserrat.cat/en/).
- **Teatre-Museu Dalí**, consultado el 23/11/2026 en la [web oficial](https://www.salvador-dali.org/en/visit/dali-theatre-museum/): entrada general 18,50 € y reducida para mayores de 65 años 15 €. El planificador solo recoge el número total de viajeros y por eso no aplica automáticamente la tarifa reducida.
- **Château Comtal de Carcasona**, consultado el 23/11/2026 en la [Forteresse royale](https://www.remparts-carcassonne.fr/en/): entrada adulta publicada a 13 €. El cálculo aplica esa tarifa adulta a cada viajero; comprueba descuentos, movilidad y horario antes de reservar.
- Las referencias de tren de Francia se consultaron en [SNCF Connect](https://www.sncf-connect.com/en-en/train/route/barcelona/perpignan), [Montpellier](https://www.sncf-connect.com/en-en/train/route/barcelona/montpellier), [Carcasona](https://www.sncf-connect.com/en-en/train/route/barcelona/carcassonne) y [Lyon](https://www.sncf-connect.com/en-en/train/route/barcelona/lyon). El importe “desde” se ofrece solo en algunas fechas y es de ida, segunda clase y sujeto a disponibilidad.
- El resto de actividades, transportes y eventos puede figurar como orientativo o pendiente de confirmar. Los enlaces a plataformas de tours sirven para consultar ofertas por fecha; sus precios no se incorporan al total.

Las fotografías de las fichas francesas y algunas fichas cercanas (Girona, Vic, Montserrat y Figueres) provienen de Wikimedia Commons. Cada imagen incluye un enlace a su ficha de autoría y licencia (CC BY, CC BY-SA o CC0). Las imágenes heredadas del catálogo usan URLs de Unsplash.

Esta versión no necesita PostgreSQL: no guarda perfiles, reservas ni precios consultados. Si se incorporan fuentes tarifarias reales, se podrá añadir una tabla propia para caché, fecha de consulta y fuente, sin modificar las tablas internas de n8n.
