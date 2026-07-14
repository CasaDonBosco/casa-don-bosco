# E.P.E.S Casa Don Bosco Servicios — Sitio web

Sitio web estático de la **Casa Don Bosco** de Naguanagua (Carabobo, Venezuela):
Casa Hogar de protección salesiana y Centro de Capacitación Laboral con más de
75 años de trayectoria.

> _"La educación es cosa del corazón"_ — San Juan Bosco

## Tecnología

HTML + CSS estáticos. Sin framework, sin JavaScript de aplicación y sin paso de
compilación. Diseñado para alojarse en **GitHub Pages**.

## Estructura rápida

- `index.html`, `quienes-somos.html`, `cursos.html` — páginas principales.
- `cursos/` — 10 páginas de curso.
- `assets/css/casa-don-bosco.css` — sistema de diseño (tokens y componentes).
- `assets/css/site.css` — maquetación de página.
- `assets/img/` — logo y favicon.
- `design/` — material de diseño original (referencia).
- `CONTEXTO.md` — información y textos de la institución (fuente del contenido).

## Ejecutar en local

Al ser estático, basta abrir `index.html` en el navegador. Para navegar con rutas
correctas, servirlo con un servidor simple:

```bash
python3 -m http.server 8000
# luego abrir http://localhost:8000
```

## Publicación

Ver **HANDOFF.md** para la guía paso a paso de despliegue en GitHub Pages.

## Documentación

- **CLAUDE.md** — guía técnica y convenciones para editar el sitio.
- **HANDOFF.md** — estado, pendientes y publicación.
