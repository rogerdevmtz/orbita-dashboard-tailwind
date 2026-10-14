# Órbita — Dashboard en Tailwind CSS v4

Proyecto educativo de 4Geeks Academy. Dashboard con datos de ejemplo para una creadora con tres productos en Instagram, TikTok y YouTube. Parte de la plantilla oficial https://github.com/4GeeksAcademy/html-hello.

## Abrir

Abre index.html en el navegador, con conexión a Internet para cargar el CDN de Tailwind v4. También puedes ejecutar desde esta carpeta:

```sh
python -m http.server 5500 --bind 127.0.0.1
```

Visita http://127.0.0.1:5500. Python sirve los archivos durante el desarrollo; no es una dependencia del dashboard.

## Requisitos implementados

- HTML semántico y Tailwind CSS v4, sin CSS personalizado ni JavaScript de aplicación.
- Superior: cuatro KPIs (comisiones, ventas, conversión y engagement).
- Intermedio: tres drivers (plataformas, productos y engagement).
- Inferior: tabla de seis campañas, detalles desplegables y totales.
- Mobile-first con sm, md, lg y xl. Las columnas secundarias se consultan en los detalles de campaña cuando no caben.
- Enlaces internos con estado de sección, etiquetas de navegación, enlace para saltar al contenido, foco visible y detalles nativos de HTML accesibles con teclado.
- Filtros por plataforma que actualizan las filas visibles, el contador y los totales de la tabla, sin JavaScript.
- Cálculos de KPI desplegables, información del período y feedback de campañas abiertas.

## Datos ficticios: septiembre de 2026

| Producto | Precio | Ventas | Comisión por venta | Total comisiones |
| -------- | -----: | -----: | -----------------: | ---------------: |
| A        |   50 € |    200 |             7,50 € |          1.500 € |
| B        |  120 € |    100 |               18 € |          1.800 € |
| C        |   80 € |    100 |               12 € |          1.200 € |
| Total    |        |    400 |                    |          4.500 € |

- Comisiones = ventas × precio × 15 %.
- Conversión = ventas / alcance × 100 = 0,20 %.
- Engagement = interacciones / alcance × 100 = 6,5 %.
- Interacciones: Instagram 3.000, TikTok 8.000, YouTube 2.000.
- Alcance: Instagram 60.000, TikTok 100.000, YouTube 40.000.
- Retorno = comisiones / costes = 4.500 / 1.500 = 3,00×. No equivale al ROI neto.
- El alcance suma campañas y no deduplica personas entre plataformas.

## Entrega

El archivo principal es index.html. Tailwind genera los estilos y media queries desde las clases utilizadas, conforme a la restricción de no escribir CSS personalizado.

Repositorio de entrega: [rogerdevmtz/orbita-dashboard-tailwind](https://github.com/rogerdevmtz/orbita-dashboard-tailwind).

La rama del proyecto es `codex/dashboard-tailwind`. El remoto `origin` apunta al repositorio propio y `template` conserva la plantilla de 4Geeks.

## Diseño

Diseño realizado a partir de la referencia visual proporcionada por el usuario: fondo negro, rail lateral compacto, cuatro KPIs con miniaturas de color, tres paneles centrales, tabla de campañas y un indicador circular de margen. Superficies oscuras, reflejos cálidos, tarjetas redondeadas, barras rojas y gauge naranja. Todo el estilo está expresado en utilidades de Tailwind v4, incluyendo degradados; no hay CSS personalizado ni dependencias visuales.

El contenido sigue el reto de la influencer: se conservan los productos A/B/C, la comisión del 15 %, las seis campañas y las fórmulas. Las miniaturas de los KPIs son motivos decorativos, sin una serie temporal asociada. Las barras grandes representan las comisiones de cada producto. El indicador circular representa (4.500 − 1.500) / 4.500 = 66,7 % de margen después de publicidad.

En móvil, la navegación se sitúa arriba, los KPIs pasan a una o dos columnas y los paneles se apilan. Se mantienen accesibles las columnas secundarias de la tabla mediante los detalles nativos de cada campaña.

## Experiencia de usuario

| Before                                           | After                                                                                                   | Why                                                                  |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Tabla con seis filas fijas                       | Filtros nativos Todas / Instagram / TikTok / YouTube                                                    | Comparar las campañas de una plataforma sin perder el resumen global |
| Totales únicos                                   | Totales y contador que corresponden a la selección                                                      | Evitar atribuir las cifras globales a una sola plataforma            |
| Iconos de navegación sin indicación de ubicación | Sección seleccionada, breadcrumb coherente y etiquetas visibles en móvil o con hover/foco en escritorio | Facilitar la orientación y el reconocimiento de cada enlace          |
| KPIs sin explicación directa                     | Cálculos desplegables, con una sola explicación abierta a la vez                                        | Entender las cifras sin abandonar la pantalla                        |
| Filas abiertas con apariencia idéntica           | Chevron, fondo y borde que indican expansión                                                            | Distinguir qué campaña se está consultando                           |
| Controles sin feedback de pulsación              | Compresión sutil del 3 % durante 150 ms                                                                 | Confirmar la pulsación sin mover los gráficos ni retrasar el teclado |

Los filtros afectan únicamente a la tabla. Los cuatro KPIs, los tres drivers y el margen continúan mostrando todas las redes; el texto junto a los filtros lo indica explícitamente. Las radios nativas permiten cambiar la selección con las flechas del teclado y regresar a Todas para restablecer la tabla.

La implementación utiliza `details` / `summary`, radios con `fieldset` / `legend` y variantes de Tailwind basadas en `:checked`, `:has()` y `:target`. No se añade JavaScript de aplicación ni CSS manual. El período permanece fijo del 1 al 30 de septiembre de 2026, de acuerdo con los datos de ejemplo.

El único movimiento es el feedback de pulsación: escala 0,97, duración 150 ms, curva cubic-bezier(0.23, 1, 0.32, 1), limitado a las transiciones de transform. Con foco visible de teclado la respuesta es inmediata; con `prefers-reduced-motion: reduce` se omite el movimiento. No se animan cifras, gráficos, altura de filas ni el scroll de navegación.

### Totales comprobados para cada filtro

| Plataforma | Campañas | Alcance | Ventas |   Coste | Comisiones | Retorno |
| ---------- | -------: | ------: | -----: | ------: | ---------: | ------: |
| Todas      |        6 | 200.000 |    400 | 1.500 € |    4.500 € |   3,00× |
| Instagram  |        2 |  60.000 |    120 |   450 € |    1.320 € |   2,93× |
| TikTok     |        2 | 100.000 |    190 |   550 € |    1.740 € |   3,16× |
| YouTube    |        2 |  40.000 |     90 |   500 € |    1.440 € |   2,88× |

Se contrastaron estos totales con las sumas de las filas de la tabla en el navegador. También se verificaron los cuatro cálculos de KPI, las seis campañas por teclado, el foco de navegación, la información del período y los filtros con movimiento reducido. Estas mejoras conservan los tres bloques y las tecnologías exigidas por la rúbrica.

## Verificación de la rúbrica

| Criterio             | Implementación                                                                                                               | Comprobación                                                                                            |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| HTML semántico       | Un main y un h1, header, nav, aside, section y siete article, table con caption, thead, tbody, tfoot y encabezados scope=col | html-validate sin errores                                                                               |
| Tailwind CSS v4      | CDN oficial browser@4; clases utility, flex/grid y breakpoints; sin CSS manual ni otros frameworks                           | Inspección de código y DOM                                                                              |
| Layout y componentes | Cuatro KPIs arriba, tres drivers en el centro, campañas debajo; tarjetas con patrones compartidos                            | Inspección visual en Chrome                                                                             |
| Responsividad        | Base móvil; sm, md, lg y xl; columnas de tabla prioritarias y detalles HTML                                                  | 320, 390, 640, 768, 1024, 1152, 1280 y 1440 px, sin desbordamiento horizontal                           |
| Accesibilidad de uso | Enlace para saltar al main, foco visible, navegación por anclas, desplegables nativos                                        | Seis campañas y cuatro cálculos de KPI por teclado; filtros con flechas; movimiento reducido comprobado |
| Datos de ejemplo     | Productos A/B/C a 50/120/80 €, comisión del 15 %, cifras consistentes                                                        | 400 ventas; 30.000 € vendidos; 4.500 € en comisiones; 1.500 € de costes                                 |

Las capturas de móvil, tablet y escritorio están en `docs/`. No se han probado dispositivos físicos ni otros motores de navegador. La entrega usa el CDN requerido por el enunciado; Tailwind genera las media queries de sus clases responsive, sin CSS personalizado.

Para repetir la validación de HTML, de forma opcional y sin añadir dependencias al proyecto:

```sh
npx --yes html-validate index.html
```

Revisión adicional guiada por las [Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines/blob/main/command.md), aplicando únicamente las reglas compatibles con el requisito de HTML y Tailwind.

Capturas: [móvil](docs/mobile.jpg) · [tablet](docs/tablet.jpg) · [escritorio](docs/desktop.jpg) · [filtro TikTok con campaña abierta](docs/ux-filtered.jpg).
