[LEEME-publicacion.md](https://github.com/user-attachments/files/33930974/LEEME-publicacion.md)
# CIDEC Bolivia · Landing premium — guía de entrega (Web Ideas Factory)

## Estructura de archivos
```
/index.html     Landing completa (HTML + CSS + JS en un solo archivo)
/robots.txt     Reemplazar __DOMINIO__
/sitemap.xml    Reemplazar __DOMINIO__
```
Las imágenes se sirven desde las URLs oficiales de Cloudinary (no hay que subirlas).

## Publicación
1. Subir los tres archivos a la raíz del hosting (GitHub Pages, Netlify, cPanel, etc.). Requiere HTTPS.
2. En `index.html`, dentro del `<head>`, añadir `canonical` y `og:url` con el dominio definitivo (hay un comentario "PENDIENTE DE PUBLICACIÓN").
3. Reemplazar `__DOMINIO__` en `robots.txt` y `sitemap.xml`.
4. Dar de alta el sitio en Google Search Console y enviar el sitemap.
5. Validar los datos estructurados en https://search.google.com/test/rich-results

## Dependencias externas
- Google Fonts: Fredoka (titulares, eco del logo) y Figtree (texto).
- Cloudinary (vosnx26t): logo, mascota y fotografías.
- Google Maps (iframe por dirección, solo se carga si la familia pulsa "Mostrar el mapa"; no requiere API key).
- WhatsApp (wa.me) para preinscripción, consultas y asistente.
- Sin librerías JS de terceros.

## Variables (objeto `CONFIG` en el script)
| Variable | Valor | Estado |
|---|---|---|
| whatsapp | 59178220718 | Confirmado |
| email | cidec.bolivia1@gmail.com | Confirmado |
| backendEndpoint | null | Pendiente: URL POST (JSON) de backend/CRM/correo si se contrata |
| Dominio / canonical | — | Pendiente |
| WIF (pie) | webideasfactory.com · +54 9 11 6510-4979 | Confirmado por WIF |

## Paleta (oficial del cliente)
Turquesa #0086B1 · Fucsia #FD6DAC · Blanco suave #F6F6F6. Derivados solo para contraste AA de texto: #006B8E, #0B3A4E, #B8256A y fondos suaves. El fucsia oficial nunca lleva texto blanco encima.

## Pruebas realizadas (Chromium headless, 1366 / 820 / 375 px)
**Implementado y comprobado**
- Sin errores de JavaScript en consola en los tres anchos; sin scroll horizontal.
- Un solo H1; todas las imágenes con `alt`; anclas internas sin enlaces rotos.
- FAQ visible y `FAQPage` JSON-LD idénticos (16 preguntas, texto a texto).
- Pestañas de niveles: clic, flechas, Inicio/Fin; la regla de crecimiento abre el nivel.
- Formulario: errores junto al campo, foco al primer error, teléfono/correo/edad (6 meses–6 años), turnos dinámicos por nivel, consentimientos obligatorios y de imágenes independiente, estado de carga, sin envío doble, una sola apertura de WhatsApp con mensaje completo marcado como PREINSCRIPCIÓN, confirmación honesta ("pendiente de envío").
- Privacidad: ningún dato en la URL de la página; `localStorage` solo guarda el checklist de documentos (sin datos personales ni médicos).
- Asistente Cidecsito: abre con foco en el campo, preguntas rápidas, 8 consultas libres probadas, rechaza preguntas médicas, deriva a WhatsApp cuando no tiene el dato, Escape cierra y devuelve el foco.
- Galería con visor: abrir, flechas, Escape.
- Mapa: el iframe se genera por dirección (sin coordenadas inventadas).
- `prefers-reduced-motion` desactiva animaciones.
- Sin nombres, colores ni textos de los HTML de referencia.

**Implementado, pendiente de validación externa**
- Carga real de imágenes de Cloudinary, fuentes y mapa (el entorno de prueba no tenía internet): revisar en navegador.
- Encuadre de cada imagen: las ilustraciones PNG se muestran completas (`contain`) y las fotos JPG/WEBP recortadas (`cover`); confirmar que ninguna foto pierde algo importante.
- Textos alternativos y pies de la galería se basan en el nombre de cada archivo: confirmar con CIDEC.
- Enlaces de Facebook, Instagram, TikTok, YouTube y blog (direcciones exactas proporcionadas; no se pudo abrir cada red desde el entorno de prueba).
- Enviar una preinscripción real desde un celular y verificar que llega a +591 78220718.
- Lighthouse/PageSpeed una vez publicado.

**Pendiente de integración**
- Backend, CRM o correo para registrar preinscripciones (`CONFIG.backendEndpoint`).
- Canonical, og:url, robots.txt y sitemap.xml con el dominio definitivo.

**Bloqueado por falta de credenciales o contenido**
- Embed de entrevistas: los enlaces `facebook.com/share/v/...` no son embebibles; se usan tarjetas con miniatura y botón "Ver entrevista". Para embeber haría falta la URL completa del video (`facebook.com/CIDEC.BOLIVIA/videos/ID`).

## Datos a confirmar con CIDEC
- Horarios de Sala Nido (la página muestra Bs. 650 por turno y "horarios a confirmar").
- Uso de `numero1.png` y `entrevista3.png`: no se usaron porque su contenido no está confirmado (podrían implicar afirmaciones no verificadas).
- Nombre de los medios de cada entrevista (hoy: "Entrevista a CIDEC" / "CIDEC en los medios").
- Edades específicas por nivel (no se publicaron por no estar confirmadas).

## Criterio de imágenes (v2)
- Fotos JPG/WEBP: a su tamaño real, bordes redondeados y marco blanco ajustado a la foto, sin relleno.
- PNG sin fondo: sin recuadro ni relleno; solo se redondean si la imagen trae fondo propio.
- Cidecsitos: decoración animada en las secciones (propuesta, adaptación, cámaras, galería, checklist); ya no son tarjetas.
- Nuevas fotos: higienedental.jpg (galería), aprendiendo_del_hogar.jpg y dedededede.jpg (familias), recepcion.png (quiénes somos).
- La foto de contacto.jpg es la portada del mapa: al tocarla se carga el mapa de Google.

## Mantenimiento
- Precios, turnos y niveles viven en `TURNOS` y `NIVELES` (script) y en las tablas/FAQ de HTML; al cambiar un precio, actualizar también el JSON-LD.
- Si cambia la FAQ, mantener idéntico el bloque `FAQPage`.
- Las respuestas del asistente están en el arreglo `BOT`: añadir palabras clave en `k` para nuevas preguntas.
- Revisar cada año el año del sitemap (`lastmod`) y los enlaces de redes.
