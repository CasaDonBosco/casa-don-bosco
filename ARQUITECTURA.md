# ARQUITECTURA de la página — Casa Don Bosco

Documento pensado para entender, sin necesidad de ser programador, **cómo está
construida** la página web de la Casa Don Bosco: con qué se hizo, cómo se organiza y
cómo se publica. Para ver el listado de archivos, consultar `ESTRUCTURA.md`.

## En pocas palabras

La página es un **sitio estático**: un conjunto de archivos HTML (las páginas) y CSS
(el diseño) que el navegador muestra tal cual. No hay una "aplicación" corriendo por
detrás, ni base de datos, ni un servidor que procese nada. Esto tiene varias ventajas:
es **gratis** de alojar (en GitHub Pages), es **muy rápido**, es **seguro** (no hay
nada que hackear) y es **fácil de mantener**: cualquier persona puede abrir un archivo
`.html` con un editor de texto, cambiarlo y ver el resultado recargando el navegador.

En concreto, el sitio **no** usa ningún framework (como WordPress, React o similares),
**no** requiere instalar programas ni "compilar" nada, y **no** tiene JavaScript de
aplicación. Es intencional: mantenerlo simple hace que dure años sin mantenimiento
técnico y que sea fácil de traspasar a otra persona.

## Cómo se organiza el sitio

El sitio tiene tres secciones principales —Inicio, Quiénes Somos y Cursos— más una
página propia para cada uno de los diez cursos. La página de Inicio presenta la doble
misión de la institución (Casa Hogar y Centro de Capacitación) y destaca algunos
cursos; "Quiénes Somos" cuenta la historia y la misión; y "Cursos" muestra el catálogo
completo en tarjetas, cada una enlazada a su página de detalle.

Todas las páginas comparten la **misma cabecera** (la cinta superior con el lema y los
teléfonos, y el menú de navegación) y el **mismo pie de página** (con los datos de
contacto). Así el visitante siempre tiene el menú a mano y una imagen coherente.

## El diseño: dos hojas de estilo

Toda la apariencia se controla desde la carpeta `assets/css/`, con dos archivos que
cumplen papeles distintos:

- **`casa-don-bosco.css` — la identidad visual.** Define los colores de marca (la
  paleta azul con degradados), las tipografías (Caprasimo para los títulos y Figtree
  para el texto), las formas redondeadas y los "componentes" reutilizables (botones,
  tarjetas, etiquetas, etc.). Es la "fuente de verdad" del look: si se cambia un color
  aquí, cambia en todo el sitio.
- **`site.css` — la maquetación.** Define cómo se acomodan los elementos en cada
  página: la portada (hero), las rejillas de tarjetas, la cabecera, el pie y el menú
  para teléfonos. Es decir, la distribución del espacio.

Esa separación es a propósito: el "qué se ve" (identidad) está separado del "dónde se
ubica" (maquetación), lo que facilita hacer cambios sin romper nada.

Un detalle del diseño: los colores, tamaños y espacios están guardados como
**variables** (llamadas *tokens*) al inicio del CSS. Cambiar el color azul principal en
un solo lugar actualiza automáticamente botones, enlaces, degradados y más. Además,
todas las fotografías se muestran con un efecto "lavado" (ligeramente desaturadas) para
que se integren con la estética azul, y los íconos son dibujos vectoriales incrustados
directamente en las páginas (no imágenes sueltas), por lo que siempre se ven nítidos.

## Cómo se repiten la cabecera y el pie

Como el sitio no usa un sistema de plantillas, **cada página incluye su propia copia**
de la cabecera y del pie. La ventaja es la simplicidad; la contrapartida es que, si
algún día se cambia el menú o el pie, hay que repetir ese cambio en todas las páginas.
Está documentado en `CLAUDE.md` para quien haga mantenimiento.

## Rutas relativas (por qué funciona igual en la PC y publicado)

Las páginas enlazan sus estilos e imágenes con **rutas relativas** (por ejemplo,
`assets/css/site.css` desde la raíz, o `../assets/...` desde las páginas de cursos).
Gracias a esto el sitio funciona tanto abriéndolo en la computadora como publicado en
GitHub Pages, que lo sirve dentro de una subcarpeta con el nombre del repositorio.

## Se adapta al teléfono, sin JavaScript

El diseño es **responsivo**: se reacomoda para verse bien en computadora, tablet y
teléfono. En pantallas pequeñas, el menú se convierte en un botón de "hamburguesa" que
despliega las opciones. Esto se logra solo con CSS (un truco con casillas de
verificación), sin necesidad de programación, lo que mantiene el sitio ligero.

## El objetivo de conversión: la preinscripción

El llamado a la acción principal en todo el sitio es el botón **"Preinscríbete ¡YA!"**,
que abre el formulario de preinscripción de Google en una pestaña nueva. Es el único
mecanismo de captación y aparece de forma consistente en la cabecera, en cada página de
curso y en las secciones de cierre.

## De dónde salen los textos

Todo el contenido (historia, misión y descripciones de los cursos) proviene de
`CONTEXTO.md`, que recopila y limpia la información del sitio original. Si el cliente
entrega datos nuevos (duración o costo de cursos, fechas, fotos reales, redes sociales),
la recomendación es actualizar tanto las páginas como `CONTEXTO.md`, para mantener una
única fuente de información.

## Las imágenes son temporales

Mientras no haya fotos propias, el sitio usa **imágenes de banco (stock)** que se cargan
desde internet. Si alguna no cargara, se muestra un bloque azul de respaldo en lugar de
un ícono roto. Están pensadas para reemplazarse fácilmente por fotografías reales de los
talleres e instalaciones.

## Dónde vive y cómo se publica

El sitio se aloja en **GitHub Pages**, el servicio gratuito de GitHub para páginas
estáticas. Los archivos se suben a un repositorio y GitHub los publica en una dirección
pública. No hay costo de hosting ni de dominio (salvo que se decida comprar un dominio
propio más adelante). El paso a paso de publicación está en `GUIA-GITHUB.md` (y su
versión `GUIA-GITHUB.pdf`).

## Cómo se hacen cambios

Para un cambio pequeño (corregir un texto, cambiar un teléfono), se edita directamente
el archivo `.html` correspondiente. Para cambiar colores o tipografías en todo el sitio,
se editan las variables al inicio de `casa-don-bosco.css`. Para añadir un curso nuevo,
se duplica una página existente de `cursos/`, se ajusta su contenido y se agrega su
tarjeta en `cursos.html`. Tras cualquier cambio, se vuelve a subir a GitHub y el sitio
publicado se actualiza en un par de minutos.

## Qué queda pendiente

El sitio está completo y funcional. Las decisiones que dependen del cliente (fotos
reales, duración y costo de cada curso, correo, WhatsApp, redes sociales, dirección
exacta y mapa) están listadas en `HANDOFF.md`.

## Resumen de ventajas de este enfoque

Es gratis de alojar, muy rápido de cargar, seguro por no tener partes dinámicas, fácil
de mantener por cualquier persona con nociones básicas de HTML, y sencillo de traspasar,
porque no depende de servicios de pago ni de tecnologías que caduquen pronto.
