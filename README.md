# Órbita — Dashboard en Tailwind CSS v4

Proyecto educativo de 4Geeks Academy. Dashboard estático para una creadora con tres productos en Instagram, TikTok y YouTube. Parte de la plantilla oficial https://github.com/4GeeksAcademy/html-hello.

## Abrir

Abre index.html en el navegador, con conexión a Internet para cargar el CDN de Tailwind v4. También puedes ejecutar desde esta carpeta:

```sh
python -m http.server 5500 --bind 127.0.0.1
```

Visita http://127.0.0.1:5500. Python sirve los archivos durante el desarrollo; no es una dependencia del dashboard.

## Requisitos implementados

- HTML semántico y Tailwind CSS v4, sin CSS personalizado ni JavaScript de aplicación.
- Superior: tres KPIs (comisiones, ventas y conversión).
- Intermedio: tres drivers (plataformas, productos y engagement).
- Inferior: tabla de seis campañas, detalles desplegables y totales.
- Mobile-first con sm, md, lg y xl. Las columnas secundarias se consultan en los detalles de campaña cuando no caben.
- Enlaces internos, enlace para saltar al contenido, foco visible y detalles nativos de HTML accesibles con teclado.

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

## Verificación de la rúbrica

| Criterio | Implementación | Comprobación |
| --- | --- | --- |
| HTML semántico | Un main y un h1, header, nav, aside, tres section, seis article, table con caption, thead, tbody, tfoot y encabezados scope=col | html-validate sin errores |
| Tailwind CSS v4 | CDN oficial browser@4; clases utility, flex/grid y breakpoints; sin CSS manual ni otros frameworks | Inspección de código y DOM |
| Layout y componentes | Tres KPIs arriba, tres drivers en el centro, campañas debajo; tarjetas con patrones compartidos | Inspección visual en Chrome |
| Responsividad | Base móvil; sm, md, lg y xl; columnas de tabla prioritarias y detalles HTML | 320, 390, 640, 768, 1024, 1280 y 1440 px, sin desbordamiento horizontal |
| Accesibilidad de uso | Enlace para saltar al main, foco visible, navegación por anclas, desplegables nativos | Seis campañas abiertas mediante Enter a 320 px, fórmulas comprobadas con teclado |
| Datos de ejemplo | Productos A/B/C a 50/120/80 €, comisión del 15 %, cifras consistentes | 400 ventas; 30.000 € vendidos; 4.500 € en comisiones; 1.500 € de costes |

Las capturas de móvil, tablet y escritorio están en `docs/`. No se han probado dispositivos físicos ni otros motores de navegador. La entrega usa el CDN requerido por el enunciado; Tailwind genera las media queries de sus clases responsive, sin CSS personalizado.

Para repetir la validación de HTML, de forma opcional y sin añadir dependencias al proyecto:

```sh
npx --yes html-validate index.html
```

Revisión adicional guiada por las [Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines/blob/main/command.md), aplicando únicamente las reglas compatibles con el requisito de HTML y Tailwind.

Capturas: [móvil](docs/mobile.jpg) · [tablet](docs/tablet.jpg) · [escritorio](docs/desktop.jpg).
