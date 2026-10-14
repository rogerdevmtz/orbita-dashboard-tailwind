# Órbita — Dashboard en Tailwind CSS v4

Proyecto educativo de 4Geeks Academy para una creadora que promociona tres productos en Instagram, TikTok y YouTube. Parte de la [plantilla oficial html-hello](https://github.com/4GeeksAcademy/html-hello).

## Abrir

Abre `index.html` con conexión a Internet para cargar Tailwind v4 desde el CDN. También puedes servir esta carpeta:

```sh
python -m http.server 5500 --bind 127.0.0.1
```

Visita http://127.0.0.1:5500. Python solo sirve los archivos durante el desarrollo.

## Estructura y requisitos

- HTML semántico: header, navegación, main, secciones, artículos y tabla con encabezados y totales.
- Cuatro KPIs: comisiones, ventas, conversión y engagement.
- Tres drivers: comparación de productos, retorno por plataforma y engagement por plataforma.
- Tabla operativa de seis campañas con filtros y detalles nativos.
- Tailwind CSS v4 exclusivamente para los estilos; sin CSS manual, JavaScript de aplicación ni otros frameworks.
- Diseño mobile-first con sm, md, lg y xl. Tailwind genera las media queries desde sus utilidades.
- Precios A/B/C de 50/120/80 € y comisión del 15 %.

## Diseño e interacción

La referencia proporcionada guía el fondo negro, las tarjetas oscuras redondeadas, el reflejo cálido, las barras de color y el indicador circular naranja.

En móvil, los cuatro KPIs forman un grupo horizontal deslizable con ajuste por tarjeta. Se ve parte de la siguiente tarjeta y una pista breve indica cómo descubrir las demás. El grupo recibe foco y admite flechas del teclado; los botones de ayuda también llevan el foco a cada tarjeta. Solo este grupo se desplaza horizontalmente, sin ampliar el ancho de la página. Desde sm se muestran dos columnas y desde lg, cuatro.

La navegación permanece fija: menú inferior en móvil y rail lateral en escritorio. El contenido reserva espacio para evitar que el menú tape la última sección.

Las mini barras de los KPIs representan valores reales por plataforma, en el orden Instagram, TikTok y YouTube. Cada barra tiene un tooltip con la red, su valor exacto y su contribución al total o los datos usados en el cálculo; admite hover, pulsación y teclado. El gráfico de productos permite cambiar entre comisiones y unidades vendidas, ajustando las alturas y la escala. Las ayudas contextuales explican las fórmulas y los productos sin añadir paneles redundantes. Se abren al pulsar o con Enter y se cierran con Escape o al pulsar fuera. En móvil se centran para no salirse de la pantalla; en escritorio se anclan al control.

Los filtros Todas / Instagram / TikTok / YouTube actualizan las filas, el contador y los totales de la tabla. Los KPIs y drivers siguen mostrando todas las redes; el texto junto a los filtros lo aclara. Las columnas secundarias se consultan en los detalles de campaña cuando no caben.

Se utilizan radios, fieldset, legend, details/summary, popover y variantes de Tailwind basadas en :checked, :has() y :target. Las ayudas usan las capacidades nativas de navegadores modernos. Hay enlace para saltar al contenido, nombres accesibles y foco visible.

El feedback de pulsación usa una escala de 0,97 durante 150 ms. Se omite con movimiento reducido y con foco visible de teclado. Las cifras y las alturas de los gráficos cambian de inmediato.

## Datos ficticios: septiembre de 2026

| Producto | Precio | Ventas | Comisión por venta | Comisiones |
| --- | ---: | ---: | ---: | ---: |
| A | 50 € | 200 | 7,50 € | 1.500 € |
| B | 120 € | 100 | 18 € | 1.800 € |
| C | 80 € | 100 | 12 € | 1.200 € |
| Total | | 400 | | 4.500 € |

- Comisiones = ventas × precio × 15 %; ventas brutas de 30.000 €.
- Conversión = 400 ventas / 200.000 de alcance × 100 = 0,20 %.
- Engagement = 13.000 interacciones / 200.000 de alcance × 100 = 6,5 %.
- Retorno = comisiones / publicidad = 4.500 / 1.500 = 3,00×; no equivale al ROI neto.
- Margen después de publicidad = (4.500 − 1.500) / 4.500 = 66,7 %.
- El alcance suma campañas; no deduplica personas entre redes.

| Plataforma | Campañas | Alcance | Ventas | Coste | Comisiones | Retorno |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Todas | 6 | 200.000 | 400 | 1.500 € | 4.500 € | 3,00× |
| Instagram | 2 | 60.000 | 120 | 450 € | 1.320 € | 2,93× |
| TikTok | 2 | 100.000 | 190 | 550 € | 1.740 € | 3,16× |
| YouTube | 2 | 40.000 | 90 | 500 € | 1.440 € | 2,88× |

## Verificación de la rúbrica

| Criterio | Evidencia |
| --- | --- |
| Semántica | HTML validado con html-validate; un main y un h1, jerarquía de títulos y tabla semántica |
| Tailwind v4 | CDN browser@4, utilidades flex/grid y responsive; sin estilos manuales ni otros frameworks |
| Tres bloques claros | Cuatro KPIs, tres drivers y tabla operativa |
| Responsividad | Chrome a 320, 390, 640, 768, 1024, 1152, 1280 y 1440 px sin desbordamiento de página |
| Uso y accesibilidad | Filtros, detalles y ayudas por teclado; Escape, cierre exterior, foco visible y movimiento reducido |
| Coherencia de datos | Totales de cada filtro contrastados con las filas; fórmulas y escalas de gráficos verificadas |

El carrusel móvil se comprobó con teclado hasta el último indicador y con las ayudas abiertas. La cuadrícula de tablet y escritorio conserva los cuatro indicadores. No se han probado dispositivos físicos ni otros motores de navegador.

Validación opcional, sin añadir dependencias al proyecto:

```sh
npx --yes html-validate index.html
```

Capturas: [móvil](docs/mobile.jpg), [tablet](docs/tablet.jpg), [escritorio](docs/desktop.jpg), [filtro TikTok](docs/ux-filtered.jpg).

## Entrega

Archivo principal: `index.html`. [Repositorio de entrega](https://github.com/rogerdevmtz/orbita-dashboard-tailwind), rama `codex/dashboard-tailwind`. El remoto origin apunta al repositorio propio y template conserva la plantilla oficial.
