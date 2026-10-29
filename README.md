# Plantilla NoExpertise · Joyería y artesanía

Web a ancho completo para joyerías y talleres artesanos, con fotos de producto a sangre y vitrina.

- Sectores: joyeria, artesania, relojeria, ceramica, taller-artesano. Estilo: refinado. Plan mínimo: presencia.
- Secciones: hero, colecciones, piezas, sobre, proceso, encargos, galeria, opiniones, preguntas, contacto (y `texto` para apartados nuevos).
- Listas propias: `colecciones` {nombre, texto, detalle, imagen} y `piezas` {nombre, texto, precio, material, categoria, estado, imagen}.
- Ejemplo: Azahar Joyería, taller de joyería y filigrana en la judería de Córdoba (negocio ficticio).
- SEO de base incluido (`src/lib/seo.ts`): canónica, og:image, JSON-LD del negocio (`JewelryStore`) y de las preguntas frecuentes, `robots.txt`, `sitemap.xml` y `llms.txt`; `noindex` si `seo.indexable: false`.
- Contenido editable en `site.yaml`; metadatos y guion del asistente en `template.yaml`; fotos a generar en `fotos.json`; reglas para el agente en `CLAUDE.md`; brief de diseño en `DISEÑO.md`.

```
npm ci
npm run dev      # desarrollo
npm run build    # web estática en dist/
```

Basada en [AstroWind](https://github.com/onwidget/astrowind) © onWidget, licencia MIT (`LICENSE-ASTROWIND.md`). Imágenes de relleno (`public/placeholders/`) dibujadas para esta plantilla, sin licencias de terceros.
