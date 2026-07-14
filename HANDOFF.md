# HANDOFF — Sitio web Casa Don Bosco

Documento de traspaso. Resume qué está hecho, qué falta y cómo publicar el sitio
en GitHub. Escrito para alguien sin experiencia técnica.

---

## 1. Estado actual

Sitio web **completo y funcional**, listo para publicar. 13 páginas:

- **Inicio** — presentación de la Casa Hogar y del Centro de Capacitación, con los
  cursos destacados y llamados a preinscripción.
- **Quiénes Somos** — historia (75+ años), misión y el trinomio "Alegría, estudio
  y piedad".
- **Cursos** — índice con los 10 cursos por categoría.
- **10 páginas de curso**, una por programa, con descripción completa, lo que se
  aprende y un panel lateral con datos y botón de preinscripción.

Diseño responsivo (se ve bien en teléfono, tablet y computadora), con la identidad
visual salesiana (azul, formas redondeadas, tipografías Caprasimo y Figtree) y menú
móvil. Todo el contenido está en español y con las erratas del sitio viejo corregidas.

---

## 2. Lo que falta / decisiones del cliente

Para dejar el sitio 100% definitivo conviene conseguir del cliente:

| Pendiente | Estado hoy en el sitio |
|---|---|
| **Fotos reales** de talleres, instalaciones y estudiantes | Se usan fotos de banco (stock) temporales, fáciles de reemplazar. |
| **Duración y costo** de cada curso | Solo Corte y Costura (5 meses) y Lab. Clínico (con pasantías) tienen dato. El resto dice "Presencial / sin experiencia previa". |
| **Fechas de inicio** de cursos | No se muestran. |
| **Correo electrónico** oficial | No aparece. |
| **WhatsApp** oficial | Hay un botón preparado, pero conviene confirmar el número. |
| **Redes sociales** (Instagram/Facebook) | Solo está YouTube. |
| **Dirección exacta + mapa** | Se indica "Naguanagua, Redoma de Guaparo". Falta dirección precisa y un mapa embebido. |
| **Logo vectorial** en alta resolución | Se usó `Logo.png` optimizado; ideal tener el vector. |

Cómo reemplazar una foto: sustituye la imagen manteniendo el mismo enlace, o cambia
el `src` de la etiqueta `<img>` por la ruta de una foto propia guardada en
`assets/img/`. Ver `CLAUDE.md`.

---

## 3. Publicar en GitHub Pages (paso a paso)

El sitio se alojará en la cuenta de GitHub **pablojbritod@gmail.com**. No hace falta
compilar nada: GitHub sirve los archivos tal cual.

### Opción A — Desde la web de GitHub (más sencilla)

1. Inicia sesión en https://github.com con la cuenta del proyecto.
2. Crea un repositorio nuevo (botón **New**). Sugerencia de nombre:
   `casa-don-bosco` o `epes-casa-don-bosco`. Márcalo **Public**.
3. En el repo vacío, usa **Add file → Upload files** y arrastra **todo** el contenido
   de esta carpeta (index.html, cursos.html, quienes-somos.html, la carpeta `cursos/`
   y la carpeta `assets/`). Confirma con **Commit changes**.
4. Ve a **Settings → Pages**.
5. En **Build and deployment → Source** elige **Deploy from a branch**.
6. En **Branch** selecciona `main` (o `master`) y carpeta `/ (root)`. Guarda.
7. Espera 1–2 minutos. GitHub mostrará la URL pública, del tipo:
   `https://pablojbritod.github.io/casa-don-bosco/`

### Opción B — Con Git (si se prefiere terminal)

```bash
git init
git add .
git commit -m "Sitio Casa Don Bosco"
git branch -M main
git remote add origin https://github.com/<usuario>/<repo>.git
git push -u origin main
```

Luego activa Pages en **Settings → Pages** igual que en la Opción A.

### Dominio propio (opcional)

Si más adelante se compra un dominio (p. ej. `casadonbosco.org`), en
**Settings → Pages → Custom domain** se escribe el dominio y se crea un archivo
`CNAME` con ese nombre. Requiere configurar DNS con el proveedor del dominio.

---

## 4. Qué necesito de ti para avanzar (GitHub)

Para ayudarte a **publicarlo yo mismo** o dejarlo automatizado, indícame:

1. **¿El repositorio ya existe o lo creamos nuevo?** Si existe, pásame la URL
   (`https://github.com/usuario/repo`).
2. **Nombre deseado del repositorio** (si es nuevo). Ej.: `casa-don-bosco`.
3. **¿Público o privado?** (Para GitHub Pages gratuito conviene público).
4. **Usuario de GitHub** de la cuenta `pablojbritod@gmail.com` (el nombre que aparece
   en la URL del perfil), para saber cómo quedará la dirección del sitio.
5. Si quieres que yo haga el `push` por ti, necesitaré que conectes el conector de
   GitHub o que me proporciones acceso; dime cuál prefieres y te guío.

Con eso te dejo el sitio publicado y te confirmo la URL final.

---

## 5. Mantenimiento

- Editar textos: abrir el `.html` correspondiente y cambiar el contenido. Los estilos
  no se tocan salvo que se quiera cambiar el diseño.
- Cambiar colores/tipografía globalmente: editar los tokens en
  `assets/css/casa-don-bosco.css` (`:root`).
- Añadir un curso: duplicar una página de `cursos/`, ajustar contenido, y añadir su
  tarjeta en `cursos.html` (e `index.html` si se quiere destacar).
- Guía técnica completa para IA/desarrolladores: `CLAUDE.md`.
