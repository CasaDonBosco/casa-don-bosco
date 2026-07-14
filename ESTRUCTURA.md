# ESTRUCTURA del proyecto — Sitio web Casa Don Bosco

Listado de todos los archivos y carpetas del proyecto, con una breve explicación de
para qué sirve cada uno. Sirve como mapa para ubicarse rápido dentro del sitio.

## Árbol de carpetas

```
Web-Pablo/
├── index.html                    Página de Inicio
├── quienes-somos.html            Página "Quiénes Somos" (historia y misión)
├── cursos.html                   Índice con las tarjetas de los 10 cursos
│
├── cursos/                       Una página por cada curso (10 archivos)
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
│
├── assets/                       Recursos que usan las páginas
│   ├── css/
│   │   ├── casa-don-bosco.css     Diseño: colores, tipografías y componentes
│   │   └── site.css              Maquetación: layouts, cabecera, pie y menú móvil
│   └── img/
│       ├── logo.png              Logo para el menú y el pie (optimizado)
│       ├── logo-lg.png           Logo en tamaño grande
│       └── favicon.png           Ícono que sale en la pestaña del navegador
│
├── Logo.png                      Logo original en alta resolución (archivo fuente)
│
├── README.md                     Presentación breve del repositorio
├── CLAUDE.md                     Guía técnica y reglas para editar el sitio
├── HANDOFF.md                    Traspaso: estado, pendientes y cómo publicar
├── GUIA-GITHUB.md                Guía paso a paso para publicar en GitHub Pages
├── GUIA-GITHUB.pdf               La misma guía en PDF (para imprimir o compartir)
├── CONTEXTO.md                   Toda la información y los textos de la institución
├── ESTRUCTURA.md                 Este archivo (mapa de archivos del proyecto)
├── ARQUITECTURA.md               Explicación de cómo está construida la página
│
├── .gitignore                    Lista de archivos que Git no debe subir
├── .nojekyll                     Pequeño ajuste para que GitHub Pages publique bien
│
└── design/                       Material de diseño (referencia; no es una página del sitio)
    ├── DESIGN_SYSTEM.md          Documento que describe el sistema de diseño
    ├── casa-don-bosco.css        Copia original del CSS de diseño
    └── ejemplo.html              Página de muestra con todos los componentes
```

## Qué se publica y qué no

- **Se publica como sitio web:** `index.html`, `quienes-somos.html`, `cursos.html`,
  las 10 páginas dentro de `cursos/`, y la carpeta `assets/` (estilos e imágenes).
- **No es parte visible del sitio (pero conviene conservarlo):** los archivos `.md`
  de documentación, `CONTEXTO.md`, la carpeta `design/` y el `Logo.png` original.
  Son material interno para mantener y entender el proyecto.

## Resumen en números

- **13 páginas** del sitio: 3 principales (Inicio, Quiénes Somos, Cursos) + 10 de curso.
- **2 hojas de estilo activas** en `assets/css/` (más una copia de referencia en `design/`).
- **3 imágenes** en `assets/img/` (logo, logo grande y favicon).
- **0 archivos de programación** (no hay JavaScript de aplicación ni base de datos).

## Notas

- Después de publicar con Git, la carpeta contendrá además una carpeta oculta `.git`
  (el historial de versiones). Es normal y no forma parte del sitio visible.
- Todas las páginas enlazan a las hojas de estilo con **rutas relativas**, por lo que
  el proyecto funciona igual en la PC y publicado en GitHub Pages.
- Para saber **cómo** encajan estas piezas, ver `ARQUITECTURA.md`.
