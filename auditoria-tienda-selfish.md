# Auditoría de la tienda Selfish (selfish6.mitiendanube.com)

Basada en el HTML de la página de inicio (cuerpo de la página, sin `<head>`). No incluye páginas de categoría, de producto, carrito ni checkout.

## Resumen

La **estructura está bien pensada**: el menú es completo y está bien organizado. Lo que falta es **contenido y confianza**. El inicio está casi vacío: no tiene carrusel ni banners, tiene solo 4 productos y no hay sección de marcas. Además faltan políticas, contacto y WhatsApp.

Hay que llenar, recortar y pulir; no hace falta rehacer nada.

## Lo que ya está bien ✅

- **Árbol de categorías completo** y en 3 niveles (Makeup › Cheeks › Blush), justo lo que pidió la clienta.
- Ya existen las categorías **Pre-Order**, **New / Best Sellers**, **Gifts** y **Sale & Offers**.
- **Mercado Pago** conectado con meses sin intereses (aparece "3 meses sin intereses de $416.67").
- Ya muestra **"Envío gratis"** en los productos, el aviso de **último en stock** ("¡No te lo pierdas, es el último!") y la etiqueta de agotado.
- Tiene buscador, newsletter, aviso de cookies, logo y link a Instagram.
- Los productos tienen varias fotos y descripciones con detalle (por ejemplo, el contenido de cada set).

## Problemas, por prioridad

### 🔴 Críticos: sin esto no se debe lanzar

| # | Problema | Evidencia | Arreglo |
|---|---|---|---|
| 1 | **Carrusel principal vacío** | La sección `home-slider` no tiene ni una imagen (el contador marca "0 / 0") | Subir de 3 a 5 banners: lanzamiento, envío gratis, preventa, marcas y temporada |
| 2 | **Sección de banners promocionales vacía** | `home-banner-promotional` sin imágenes ni título | Usarla para accesos rápidos por categoría (Makeup / Skincare / Haircare) o para la sección de marcas |
| 3 | **Sección de video vacía** | `home-video` sin video | Desactivarla o poner un reel de Instagram |
| 4 | **Solo hay 4 productos visibles** | "Destacados" muestra 4 productos y el producto principal repite uno de ellos | Cargar catálogo. La mayoría de las ~80 categorías del menú se verán vacías |
| 5 | **No hay políticas** | No hay ni un link a envíos, cambios y devoluciones, privacidad o términos | Crear páginas de envíos, cambios y devoluciones, preventa, privacidad, términos y preguntas frecuentes, y enlazarlas en el pie de página. Son obligatorias por confianza y por la PROFECO |
| 6 | **No hay contacto ni WhatsApp** | El tema trae el ícono de WhatsApp pero no está activado; el pie de página no tiene correo ni teléfono | Activar el botón flotante de WhatsApp. Eso resuelve directo su problema de perder ventas por tardar en contestar |

### 🟠 Importantes

| # | Problema | Arreglo |
|---|---|---|
| 7 | **No hay navegación por marcas**, que ella pidió explícitamente | Crear la categoría "Brands" (Charlotte Tilbury, Patrick Ta, Tarte, OUAI…) y mostrar una fila de logos en el inicio |
| 8 | **Menú demasiado grande para el catálogo actual**: unas 80 categorías y 4 productos | Ocultar las subcategorías vacías hasta tener productos, o empezar solo con 2 niveles. Una categoría vacía se siente como tienda abandonada |
| 9 | **"Fragance" está mal escrito** (lo correcto es "Fragrance") | Corregir el nombre y la URL `/fragance/` |
| 10 | **URLs con "1" sobrante**: `/face1/`, `/lips1/`, `/blush1/`, `/bronzer1/`, `/best-sellers1/`, `/sale-offers1/` | Limpiar las URLs (ayuda a SEO y se ve más profesional). Se generan por categorías borradas o duplicadas |
| 11 | **Mezcla de idiomas**: menú en inglés y el resto de la tienda en español | Decidir. Si el inglés es parte del estilo de la marca está bien, pero al menos los nombres de producto y las descripciones deben estar en español para que la encuentren en Google México |
| 12 | **Barra de anuncios vaga**: "¡Descuento exclusivo!" no dice cuál | Cambiarla por algo concreto: "Envío gratis en compras +$999 · 3 MSI con Mercado Pago" |
| 13 | **"Hair Perfume & Hair Mists" duplicada** en Haircare y en Fragance con distinta URL | Dejar una sola categoría y asignar los productos a ambas ramas |
| 14 | **"Sale & Offers" está dentro de Gifts** | Moverla al primer nivel del menú, porque es de lo más buscado |

### 🟡 Mejoras

- No aparece Google Analytics ni el píxel de Meta en el HTML. Falta confirmarlo en el `<head>`, que no venía en el archivo. Sin eso no hay **analítica de búsquedas**, que era otro de sus pedidos.
- El texto alternativo de las fotos se repite en automático ("- comprar en línea", "en internet"). Es mejor algo descriptivo para SEO.
- Los nombres de producto son muy largos ("Charlotte Tilbury Pillow Talk Beauty Soulmates Airbrush…") y en celular se cortan. Conviene un formato tipo "Marca – Producto – Tono/Tamaño".
- Agregar una sección "Best Sellers" o "Lo más nuevo" en el inicio, además de "Destacados".
- El pie de página solo repite el menú. Faltan formas de pago, métodos de envío, políticas y contacto.
- Agregar TikTok y Facebook si los tiene.

## Pendiente de revisar con capturas o acceso

- La página de categoría: filtros por marca, precio y tono.
- La página de producto: variantes o tonos, texto de preventa y fecha estimada.
- El carrito, el checkout y el cálculo de envíos (si ya hay paqueterías configuradas).
- La vista en celular.
- El `<head>`: título, descripción, analítica y píxel.

## Plan sugerido

1. **Día 1–2 (para poder lanzar):** carrusel y banners, políticas, WhatsApp, pie de página y barra de anuncios.
2. **Día 3–4:** marcas, limpiar el menú y las URLs, corregir "Fragrance".
3. **Día 5:** Analytics y búsquedas sin resultados, píxel de Meta y catálogo de Instagram.
4. **Mientras tanto, la clienta:** carga de productos y fotos de banners.
