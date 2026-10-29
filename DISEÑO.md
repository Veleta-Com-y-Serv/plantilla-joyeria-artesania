# Joyería y artesanía: brief de diseño

Plantilla `joyeria-artesania` creada el 29/10/2026 a partir de `portfolio` con `php artisan plantillas:nueva` y
rediseñada entera (tanda «ancho completo», fila 18). Este fichero se queda en el repo: es lo que lee quien (persona
o agente) rediseñe la plantilla.

## Brief

- **Para quién**: joyerías de autor, plateros, relojeros, ceramistas y talleres artesanos (`sectores`). Su cliente
  entra a ver piezas de cerca, saber quién las hace y pedir un encargo (alianzas, transformar una joya heredada).
- **Qué tiene que conseguir la web**: que el visitante pida cita para un encargo (botón de la cabecera, portada,
  banda de encargos con formulario) o pregunte por una pieza de la vitrina.
- **Tono y estilo** (`refinado`): elegante, cálido, artesano. Sí: el escaparate de una joyería antigua, un estuche
  de terciopelo, la ficha de una pieza en un catálogo de subasta. No: la caja centrada estrecha con tarjetas
  blancas, ni el lujo frío de clínica (blanco + oro + gris), ni la rejilla de filetes y monoespaciada de `portfolio`.
- **Concepto «estuche y vitrina»**: la web es un estuche abierto. Bandas a sangre negras (terciopelo), blanco roto
  (lino) y oro (metal pulido); fotos de producto grandes que tocan el borde de la ventana con un **filete dorado por
  dentro** (`.marco`, el cristal de la vitrina); el material de cada pieza en un **punzón** (sello ovalado,
  `.punzon`), como el contraste de la plata; colecciones y pasos numerados en **romanos en cursiva**; rombos de oro
  como marca (preguntas, pasos, favicon).
- **Paleta de ejemplo**: primario `#0e0d0b` (negro estuche: portada, vitrina, proceso, opiniones, pie), acento
  `#c9a24b` (oro: botones, filetes, banda de la declaración, mitad de encargos), fondo `#f5f0e6` (blanco roto:
  bandas claras), texto `#17150f`. Derivados con `color-mix`: marfil (fondo + 10 % de oro) para galería y contacto,
  oro legible sobre claro (oro + 48 % de texto) para antetítulos, filetes al 55 %. Aguanta otros cuatro colores si
  el primario es oscuro y el fondo claro.
- **Tipografía** (del sistema, sin descargas): títulos en serif de alto contraste («Bodoni 72», «Bodoni MT»,
  Didot; de respaldo «Palatino Linotype» y Georgia), peso normal, hasta 7 rem en la portada y 2,75 rem en móvil;
  cursiva para citas, numerales y la nota del encargo. Texto en sans humanista («Gill Sans», «Gill Sans MT»,
  Optima, Candara). Antetítulos, botones y etiquetas en mayúsculas pequeñas muy espaciadas (0,2-0,3 em) con una
  línea de oro delante.
- **Ritmo de bandas** (de arriba abajo): cabecera negra fija → portada partida (negro con titular / foto a sangre,
  88 svh; en móvil la foto llena la pantalla detrás del texto con velo) → colecciones: titular en banda clara y
  filas 50/50 en zigzag alternando clara y negra → vitrina negra con mosaico de piezas de borde a borde (2/3
  columnas) y filtro → el taller: foto 50/50 con historia y equipo, y declaración en banda dorada → proceso: franja
  de foto a sangre y pasos en negro (1/2/4 columnas) → encargos partido oro/negro con formulario → galería marfil
  con mosaico sin margen (la primera 2×2) → opiniones en negro con cita enorme → preguntas en clara partida →
  contacto marfil partido con la fachada a sangre → pie negro de cuatro columnas.

## Apartados y listas propias

| id | Qué enseña | Lista propia |
|---|---|---|
| `hero` | Titular, texto, dos botones, localidad y teléfono | — |
| `colecciones` | Las líneas del taller, una fila 50/50 cada una | `colecciones` {nombre, texto, detalle, imagen} |
| `piezas` | La vitrina con filtro por `categoria` | `piezas` {nombre, texto, precio, material, categoria, estado, imagen} |
| `sobre` | Historia, equipo y declaración | `personas` {nombre, cargo, foto} |
| `proceso` | Del boceto al pulido | `items` {titulo, texto, duracion} |
| `encargos` | Qué se encarga y formulario (tipo, fecha, mensaje) | `items` {titulo, texto} |
| `galeria` | El taller por dentro | `galeria` (rutas) |
| `opiniones` | Cita grande y opiniones | `testimonios` {texto, autor} |
| `preguntas` | Plazos, tallas, garantía, envíos | `preguntas` {pregunta, respuesta} |
| `contacto` | Fachada, teléfono, dirección, horario, formulario | — |

Todas pintan bien vacías: sin precio no hay precio, sin colecciones/opiniones/preguntas/galería no hay sección,
sin piezas la vitrina se queda en su titular, sin foto la portada se centra sobre negro.

## Fotos (`fotos.json`, 16)

Producto sobre terciopelo negro con luz cálida lateral (portada 3:4 porque la portada es partida; piezas 1:1),
colecciones sobre lino, barro de patio y mesa de taller (4:3), el banco de joyero (3:4), la mesa de trabajo en
panorámica (21:9), detalles del taller (1:1) y la fachada encalada con reja y geranios en la judería (1:1). Sin
texto legible, sin logotipos, sin personas ni manos.

## Qué no hacer

- Volver a la columna centrada con tarjetas blancas o meter sombras y esquinas redondeadas: aquí todo es recto,
  con filetes finos.
- Usar oro para texto pequeño sobre fondo claro (no llega a AA): para eso está `--oro-sobre-claro`.
- Añadir fuentes externas o JavaScript más allá del menú móvil y el filtro de la vitrina.
