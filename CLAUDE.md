# CLAUDE.md — Guía del proyecto

Sitio web de **E.P.E.S Casa Don Bosco Servicios** (Casa Hogar salesiana + Centro
de Capacitación Laboral, Naguanagua, Carabobo, Venezuela). Sitio estático, sin
framework ni paso de compilación, pensado para **GitHub Pages**.

## Qué es este repositorio

HTML estático puro + CSS. No hay JavaScript de aplicación, no hay build, no hay
dependencias que instalar. Se sirve tal cual. Cualquier persona puede editar un
`.html` con un editor de texto y ver el cambio recargando el navegador.

## Estructura

```
/
├── index.html              Inicio
├── quienes-somos.html      Quiénes Somos (historia + misión)
├── cursos.html             Índice de los 10 cursos
├── cursos/                 Una página por curso (10 archivos)
│   ├── mantenimiento-tecnico-pc.html
│   ├── operador-de-pc.html
│   ├── reposteria-y-cocina.html
│   ├── estetica-y-belleza.html
│   ├── asistente-laboratorio-clinico.html
│   ├── asistente-higiene-dental.html
│   ├── asistente-administrativo.html
│   ├── corte-costura-confeccion.html
│   ├── primeros-auxilios.html
│   └── masoterapia.html
├── assets/
│   ├── css/
│   │   ├── casa-don-bosco.css   Sistema de diseño (tokens + componentes). FUENTE DE VERDAD del look.
│   │   └── site.css            Maquetación de página (layouts, cabecera/pie, rejillas, menú móvil).
│   └── img/
│       ├── logo.png            Logo para nav/footer (~220px)
│       ├── logo-lg.png         Logo grande
│       └── favicon.png
├── design/                 Material de diseño original (referencia; NO se sirve como página).
├── CONTEXTO.md             Toda la información y textos de la institución. Fuente del contenido.
├── HANDOFF.md              Traspaso: estado, pendientes y guía de publicación.
└── README.md
```

## Reglas de diseño (no romper)

El look se define en `assets/css/casa-don-bosco.css` y en `design/DESIGN_SYSTEM.md`.
Puntos clave al editar o crear páginas:

- **Nunca** hardcodear colores hex, fuentes o tamaños que ya existan como token
  (`--color-*`, `--font-*`, `--space-*`, `--radius-*`). Usar las variables CSS.
- Paleta azul con degradados. El azul es la identidad: no desaturar a gris.
- Tipografías: **Caprasimo** (títulos) y **Figtree** (cuerpo), cargadas por
  `@import` dentro del CSS.
- Formas redondeadas: contenedores `--radius-lg`; botones/tags/inputs son píldoras
  (`border-radius: 999px`, ya aplicado por las clases).
- **Toda fotografía va envuelta en `.washed`** (desaturada) dentro de un contenedor
  con `overflow:hidden` y su radio. Ya hay un fondo de respaldo por si una imagen
  externa no carga.
- Iconos: estilo Lucide, `stroke-width: 2.75`. En el sitio están inline como SVG
  (sin JS). Si necesitas uno nuevo, cópialo de https://lucide.dev y ajústale el stroke.
- Superficies con degradado: clases `.band-gradient`, `.panel-deep`, `.footer-gradient`.

Layouts (hero, rejillas, página de curso, footer, menú móvil responsivo con el
"checkbox hack" sin JS) están en `site.css`, no en `casa-don-bosco.css`. Mantener
esa separación: `casa-don-bosco.css` = diseño; `site.css` = maquetación.

## Convenciones de las páginas

- Cada página es autónoma y **repite** la cinta superior (`.topbar`), la navegación
  (`header.site-nav`) y el pie (`footer.site-footer`). No hay includes: si cambias
  la navegación o el pie, hay que replicarlo en todas las páginas. Ver "Regenerar".
- Rutas **relativas**: las páginas raíz usan `assets/...`; las de `cursos/` usan
  `../assets/...` y `../index.html`. Respetar esto para que funcione en GitHub Pages
  (que sirve bajo `/nombre-repo/`). No uses rutas que empiecen con `/`.
- Idioma `es`. Corregir siempre las erratas del sitio original: "Servicios" (no
  "Serviciosos"), "Quiénes Somos" (con tilde y sin "??").
- CTA único de conversión: formulario de Google `https://forms.gle/pANjRrRiSZySaxhs9`
  (abre en pestaña nueva). Botón "Preinscríbete ¡YA!" consistente en todo el sitio.

## Contenido

Todo el texto proviene de `CONTEXTO.md` (transcrito del Google Sites original y
limpiado). Si el cliente entrega datos nuevos (duración/costo de cursos, fechas,
fotos reales, redes sociales), actualizar las páginas y también `CONTEXTO.md` para
mantener una única fuente.

## Regenerar el sitio (opcional)

Las 13 páginas se generaron con un script de autoría de un solo uso
(`generate.py`, no versionado en el repo) que arma cabecera/nav/pie idénticos y
rellena los cursos desde una lista de datos. El sitio servido **no** lo necesita.
Para cambios pequeños, edita el HTML directamente. Para cambios estructurales que
afecten a muchas páginas (p. ej. un ítem nuevo en el menú), lo más seguro es
regenerar. Si no tienes el script, replica el cambio a mano en cada `.html`.

## Datos de contacto vigentes

- Teléfonos: 0412-9403020 / 0424-4132666
- Ubicación: Casa Don Bosco, Naguanagua (Redoma de Guaparo), Carabobo, Venezuela
- YouTube: Coordinación Pedagógica — http://www.youtube.com/@coordinacionpedagogica-cec7384
- Preinscripción: https://forms.gle/pANjRrRiSZySaxhs9

(Pendiente de confirmar con el cliente: correo, WhatsApp oficial, redes sociales,
dirección exacta/mapa, y duración/costo/fechas por curso. Ver HANDOFF.md.)

## Despliegue

GitHub Pages desde la rama principal, raíz del repositorio. No requiere build.
Detalles paso a paso en `HANDOFF.md`.
