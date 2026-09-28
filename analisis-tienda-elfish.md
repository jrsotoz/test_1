# Tienda en línea "Elfish": análisis, arquitectura y cotización

## 1. Lo que pide, en limpio

| # | Requerimiento | Qué significa técnicamente |
|---|---|---|
| 1 | Tienda de maquillaje, skincare, haircare y wellness para mujer | E-commerce B2C, pensado primero para celular |
| 2 | Inicio con logo, carrusel de fotos, banners ("envío gratis en compras mayores a $X") y secciones como "Lo más nuevo" | Plantilla personalizada con slider, barra de anuncios y colecciones destacadas |
| 3 | Menú por categorías y subcategorías (Makeup → Face → Blush) | Categorías en 2 o 3 niveles y menú desplegable |
| 4 | Sección "Marcas" donde al dar clic salen todos los productos de esa marca | Marca como campo del producto, con filtro o página propia por marca |
| 5 | Carrito, pago y dirección de envío sin que ella intervenga | Checkout con pasarela de pago (tarjeta, OXXO, transferencia) |
| 6 | Envíos automatizados | Integración con paqueterías que calcule el costo y genere la guía sola |
| 7 | Productos en stock y también preventa o encargos | Control de inventario más productos en preorden (vender sin stock, con aviso y fecha estimada) |
| 8 | Descargar las órdenes para preparar y enviar | Panel de pedidos, exportar a CSV e imprimir guías |
| 9 | Ver qué busca la gente aunque no lo tenga (ella cree que eso son "ads") | Analítica de búsquedas internas, sobre todo las que no dieron resultados |
| 10 | Que no se le vayan ventas por tardar en contestar en Instagram | Tienda de Instagram conectada al catálogo, respuestas automáticas con link y botón de WhatsApp |
| 11 | Que se vea bonita y sea fácil para comprar | Diseño y experiencia de compra |
| 12 | Ella sube los productos | No entra en tu alcance, pero sí enseñarle a hacerlo |
| — | Le importan las comisiones y ya tiene Tiendanube avanzado al 70% | Restricción de costo, y hay trabajo previo que se puede aprovechar |

**Conclusión:** no necesita un sistema a la medida. Necesita una plataforma de e-commerce bien configurada, una plantilla bonita y algunas integraciones.

## 2. Qué arquitectura usar

**Recomendación: retomar Tiendanube**, con Shopify como plan B.

| Opción | Veredicto |
|---|---|
| **Tiendanube (retomar)** ✅ | Ya lleva el 70% y ella lo conoce. Está pensada para LATAM y tiene de fábrica envíos, pagos con OXXO, Mercado Pago e Instagram Shopping. Es la opción más barata para ella y la más rápida para ti. |
| Shopify | Es técnicamente la mejor: más apps para preventa y reportes nativos de "búsquedas sin resultados". Pero cuesta más al mes y cobra una comisión extra si no usa Shopify Payments. Proponla solo si en Tiendanube algo no se puede. |
| WooCommerce | ❌ Ella misma dijo que no le entiende. Además hay que pagar hosting, actualizar plugins y cuidar la seguridad, y tú terminarías como su soporte técnico eterno. |
| A la medida (Next.js + Stripe, etc.) | ❌ Cuesta 5 a 10 veces más, ella no podría manejarla sola y cada cambio dependería de ti. |

### Cómo quedaría armada

```
Instagram / Facebook / Google
        │  (Instagram Shopping + respuestas automáticas con link)
        ▼
  Tiendanube (plantilla personalizada)
   ├─ Inicio: barra "envío gratis +$X", carrusel, banners, "Lo más nuevo", "Más vendidos"
   ├─ Categorías: Makeup › Face › Blush / Skincare / Haircare / Wellness
   ├─ Marcas: página o filtro por marca
   ├─ Producto: stock normal o "Preventa – llega en X días"
   ├─ Checkout: Mercado Pago / Pago Nube (tarjeta, OXXO, SPEI)
   └─ Envíos: Envío Nube o Envia.com / Skydropx (cotiza y genera la guía)
        │
        ▼
  Panel de ella: pedidos → exportar CSV → imprimir guías → enviar
        │
  Google Analytics 4 + Search Console
   └─ Reporte de "qué buscan" y "qué buscan y no encuentran"
```

### Cómo resolver lo más delicado

- **Preventa:** en Tiendanube dejas el producto con stock "infinito" o permitido en negativo, más una etiqueta y un texto de "Preventa, entrega estimada X". Si ella necesita cobrar anticipos, eso requiere una app. Pregúntale antes de cotizar.
- **Búsquedas sin resultados:** Google Analytics 4 registra automáticamente lo que la gente escribe en el buscador de la tienda (lee el parámetro `?q=` de la dirección). Le agregas un pequeño script que mande un evento `search_no_results` cuando la búsqueda sale vacía. Luego le armas un reporte sencillo que ella abre desde el celular. Esto es justo lo que ella llama "ads".
- **Instagram:** conectas el catálogo para que pueda etiquetar productos en sus posts y configuras respuestas automáticas, con Meta Business Suite gratis o con ManyChat. Por ejemplo, si alguien escribe "precio", le responde con el link a la tienda. Esto ataca directo su problema de perder ventas.
- **Marcas:** usa el campo de marca del producto o una categoría padre "Marcas" con una subcategoría por marca. Pon logos en el inicio para que la gente dé clic.

## 3. Cuánto cobrarle (MXN)

### Horas estimadas

| Bloque | Horas |
|---|---|
| Revisar lo que ya avanzó y ordenar categorías, subcategorías y marcas | 4–6 |
| Diseño y personalización de la plantilla (inicio, carrusel, banners, página de producto, versión celular) | 12–18 |
| Pagos y checkout | 2–3 |
| Envíos y paqueterías, reglas de envío gratis | 3–5 |
| Preventa (etiquetas, textos, lógica) | 2–4 |
| Analytics, búsquedas sin resultados y Search Console | 3–4 |
| Instagram Shopping y respuestas automáticas | 3–5 |
| Pruebas de compra completas | 2–3 |
| Capacitación: cómo subir productos, descargar pedidos y generar guías (grabada) | 2–3 |
| **Total** | **~35–50 h** |

Con una tarifa amistosa de $250 a $350 MXN por hora sale entre **$9,000 y $17,000 MXN**.

### Propuesta por paquetes

| Paquete | Incluye | Precio sugerido |
|---|---|---|
| **Básico** | Retomar Tiendanube, categorías y marcas, diseño del inicio, pagos, envíos y capacitación | **$7,000 – $9,000** |
| **Completo** ⭐ | Todo lo básico más preventa, analítica de búsquedas, Instagram Shopping, respuestas automáticas y 2 rondas de cambios | **$12,000 – $15,000** |
| Mantenimiento (opcional) | Cambiar banners de temporada, ajustes pequeños y soporte | $800 – $1,500 al mes |

Si de verdad no le quieres cobrar mucho, el Completo en **$10,000 a $12,000** sigue siendo justo y es barato para el mercado. Una agencia le cobraría de $25,000 a $50,000 o más.

### Condiciones para que no te coman vivo

- **Pago:** 50% al iniciar y 50% al entregar.
- **Queda fuera:** subir productos, tomar o editar fotos y hacer el logo. Si quiere que subas productos, cóbralo aparte, por ejemplo $15 a $25 por producto.
- **Costos que paga ella:** el plan de Tiendanube, el dominio (unos $300 a $500 al año), las apps de pago y las comisiones de la pasarela, que andan alrededor del 3.5% + IVA. Revisa los precios vigentes antes de pasárselos.
- **Tiempo de entrega:** de 3 a 4 semanas, siempre que ella entregue a tiempo el logo, las fotos de los banners y los textos.
- **Cambios:** 2 rondas incluidas; los cambios extra se cobran por hora.

## 4. Pregúntale esto antes de cerrar el precio

1. ¿Cuántos productos y marcas va a tener, más o menos?
2. En preventa, ¿cobra el total o un anticipo? ¿Da fecha de entrega estimada?
3. ¿Qué paqueterías usa hoy y desde qué código postal envía?
4. ¿Ya tiene logo, paleta de colores y fotos para los banners?
5. ¿Qué plan de Tiendanube tiene? Algunas funciones de diseño avanzado y apps dependen del plan.
6. ¿Necesita facturar?
