# Plantilla «Joyería y artesanía» (NoExpertise)

Web estática Astro 5 + Tailwind 4, derivada de AstroWind (MIT, ver `LICENSE-ASTROWIND.md`). Estilo: **refinado**,
concepto «estuche y vitrina» a ancho completo (ver `DISEÑO.md`). Todo en castellano de España, frases cortas, sin jerga.

## Dónde está cada cosa
- **Textos, contacto, menú, SEO y secciones**: `site.yaml` (raíz). Es la única fuente de contenido. `src/data/site.ts` lo carga y lo tipa (también las listas propias `colecciones` y `piezas`); no pongas textos fijos en los componentes.
- **Colores**: `site.yaml → colores` (primario = negro de las bandas oscuras y del pie, acento = oro de botones, filetes y banda dorada, fondo = blanco roto de las bandas claras, texto). `src/layouts/Base.astro` los convierte en variables CSS (`--c-primario`…); los derivados (marfil, oro legible sobre claro, filetes) salen con `color-mix` en `src/styles/global.css`.
- **Tipografías y aspecto general**: `src/styles/global.css` (serif de alto contraste del sistema para títulos, sans humanista para el texto, bandas `.banda-clara/.banda-marfil/.banda-oscura/.banda-oro`, botones `.btn`/`.btn-sec`, `.marco` (filete de vitrina), `.punzon`, cabecera y pie). Fuentes del sistema: no añadas fuentes externas.
- **Imágenes**: en `public/`. Las fotos van en `public/fotos/` (las genera el paso de fotos a partir de `fotos.json`); los SVG de `public/placeholders/` son de respaldo. En `site.yaml` se referencian con ruta absoluta (`/fotos/portada.jpg`). Las personas del equipo llevan `/placeholders/persona.svg` hasta que el cliente sube su foto.
- **Logo**: `site.yaml → logo` (ruta en `public/`); vacío = sello con la inicial + nombre en texto.
- **Pie «Web creada con NoExpertise»**: `site.yaml → marca_pie` (true en plan gratis).

## Secciones
Cada sección es un componente que solo se pinta si `site.yaml → secciones.<id>.activa` es `true`, en el orden de `site.yaml`.
- `hero` → portada partida a sangre (texto sobre negro + foto de producto).
- `colecciones` → filas 50/50 foto/texto en zigzag; sin colecciones no se pinta.
- `piezas` → la vitrina: mosaico de piezas de borde a borde con filtro por categoría.
- `sobre` → el taller (foto 50/50, historia, equipo) y la declaración en banda dorada.
- `proceso` → franja de foto y pasos numerados en romanos.
- `encargos` → banda partida oro/negro con lo que se encarga y el formulario de encargo.
- `galeria` → mosaico de fotos sin margen.
- `opiniones` → cita enorme y opiniones en columnas; sin opiniones no se pinta.
- `preguntas` → acordeón `details/summary`; sin preguntas no se pinta.
- `contacto` → foto de la fachada, teléfono grande, datos y formulario.
- `texto` → diseño genérico para apartados nuevos (`tipo: texto`).

## Reglas para órdenes
1. **Activar o quitar una sección**: cambia `activa: true|false` en `site.yaml`. No borres componentes.
2. **Reordenar secciones**: mueve el bloque dentro de `secciones:` en `site.yaml`.
3. **Cambiar textos, teléfonos, horarios, fotos**: solo en `site.yaml`. Si un texto contiene comas o «: » dentro de `{ … }`, ponlo entre comillas. Precios siempre entre comillas (`"185 €"`, `"desde 890 € la pareja"`).
4. **Listas planas**: nunca una lista dentro de un elemento de lista; máximo 24 elementos por lista.
5. **Página nueva**: crea `src/pages/<slug>.astro` con `import Base from '../layouts/Base.astro'` y `<Base titulo="…" descripcion="…">…</Base>`; enlázala en `site.yaml → menu`. Ejemplo: `src/pages/aviso-legal.astro` (banda negra con el título y banda clara con el texto).
6. **Sección nueva**: crea `src/components/secciones/<id>.astro` (copia la estructura de una existente: `seccion(id)`, `Seccion` con su `banda`, `Titular`) y añade `secciones.<id>` en `site.yaml`. `src/pages/index.astro` la recoge sola.
7. **No tocar** `src/layouts/Base.astro`, `tailwind.config.mjs` ni `src/styles/comun.css` salvo orden explícita de diseño. Tampoco `src/lib/seo.ts` ni `src/pages/robots.txt.ts`, `sitemap.xml.ts` y `llms.txt.ts`: son el SEO de base (canónica, og:image, `noindex` si `seo.indexable: false`, JSON-LD del negocio y de las preguntas, robots, sitemap y llms.txt) y salen solos de `site.yaml`. `seo.url` y `seo.indexable` los pone la plataforma: no los cambies.
8. Mantén: `lang="es-ES"`, imágenes con `Imagen.astro` (carga diferida), JavaScript solo el pequeño en línea que hay (menú móvil y filtro de la vitrina), 16 px de margen lateral del texto (`.contenedor`), fotos y fondos de borde a borde, sin scroll horizontal en móvil, botones de 44 px de alto o más. Imágenes de contenido con `alt` sacado del contenido (`altHero`, `altFicha`, `altGaleria`, `altSeccion` de `src/lib/seo.ts`); las decorativas, `alt=""`.
9. El formulario no tiene servidor: abre el correo (`mailto`) con el email de `site.yaml`. Para envío real, cambia `action` en `src/components/ui/FormularioContacto.astro`.

## Construir
```
npm ci && npm run build      # resultado en dist/
npx astro preview            # ver dist/ en http://localhost:4321
```
Antes de dar una orden por buena: `npm run build` sin errores.

## Campos propios de esta plantilla (además del esquema común)
- `hero.cta_secundario`: segundo botón de la portada.
- `colecciones.colecciones[]`: {nombre, texto, detalle (material, sale en el punzón), imagen}; `colecciones.cta`: enlace de cada fila.
- `piezas.piezas[]`: {nombre, texto, precio, material, categoria (filtro), estado («Pieza única», «Por encargo» o vacío), imagen}.
- `sobre.declaracion`: la frase de la banda dorada; `sobre.personas[]`: {nombre, cargo, foto}.
- `proceso.items[]`: {titulo, texto, duracion}; `proceso.imagen`: franja de foto.
- `encargos.items[]`: {titulo, texto} (también son las opciones del desplegable del formulario); `encargos.nota`: frase bajo el formulario; `encargos.boton` (opcional): texto del botón.
- `opiniones.testimonios[]`: {texto, autor}; la primera sale como cita grande.
- `contacto.imagen`: foto de la fachada.
