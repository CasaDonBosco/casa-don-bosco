# Guía: publicar el sitio en GitHub Pages

Guía paso a paso para **crear el repositorio** y **publicar la página web** de Casa
Don Bosco. Al terminar, el sitio quedará en línea con una dirección pública.

- **Cuenta / usuario de GitHub:** `CasaDonBosco` (pablojbritod@gmail.com).
- **Repositorio:** lo crearemos ahora. Será **público**. Nombre sugerido: `casa-don-bosco`.
- **Dirección final del sitio:** `https://casadonbosco.github.io/casa-don-bosco/`
- **Cómo subiremos los archivos:** por **comandos Git** desde la PC (Opción B).
  También se incluye la forma manual por la web (Opción A) como alternativa.

---

## Parte 1 — Crear el repositorio (en la web de GitHub)

1. Entra en **https://github.com** e inicia sesión con la cuenta `CasaDonBosco`.
2. Arriba a la derecha, haz clic en el **`+`** y elige **New repository**
   (Nuevo repositorio).
3. Rellena el formulario:
   - **Repository name:** escribe `casa-don-bosco`.
   - **Description** (opcional): "Sitio web E.P.E.S Casa Don Bosco Servicios".
   - **Public:** déjalo marcado (es la opción que necesitamos).
   - **NO** marques "Add a README file", ni .gitignore, ni licencia. El repositorio
     debe quedar **vacío** para poder subirlo por Git sin conflictos.
4. Haz clic en **Create repository** (Crear repositorio).

Anota la dirección del repositorio, será:
`https://github.com/CasaDonBosco/casa-don-bosco.git`

---

## Parte 2 — Subir los archivos del sitio

Hay dos formas. **Usaremos la Opción B (comandos Git).** La Opción A queda como
alternativa manual por si se prefiere.

### Opción B — Por comandos Git (la que usaremos)

#### Qué información y claves necesitas tener listas

- **Git instalado** en la PC. Si no lo tienes, descárgalo de https://git-scm.com
  e instálalo con las opciones por defecto.
- **Usuario de GitHub:** `CasaDonBosco`.
- **Correo** de la cuenta de GitHub (el asociado a pablojbritod@gmail.com).
- **URL del repositorio** (de la Parte 1): `https://github.com/CasaDonBosco/casa-don-bosco.git`.
- **Un Token de Acceso Personal (PAT)** de GitHub. Desde 2021 GitHub **ya no acepta
  la contraseña normal** para subir por comandos: en su lugar pide un token. Cómo
  crearlo (una sola vez):
  1. En GitHub, arriba a la derecha: foto de perfil, luego **Settings**.
  2. En el menú de la izquierda, hasta el final: **Developer settings**.
  3. **Personal access tokens**, luego **Tokens (classic)**, luego **Generate new token (classic)**.
  4. Ponle un nombre (ej. "PC Casa Don Bosco"), una expiración (ej. 90 días) y marca
     el permiso **`repo`** (control total de repositorios).
  5. **Generate token** y **copia** el token (empieza por `ghp_...`).
     Solo se muestra una vez: guárdalo en un lugar seguro.

> En Windows, al hacer `git push` es probable que se abra una ventana del navegador
> para iniciar sesión en GitHub. Si eso ocurre, inicia sesión ahí y listo, no hará
> falta pegar el token a mano. Si en cambio la terminal te pide usuario y contraseña,
> usa `CasaDonBosco` como usuario y el token como contraseña (no la contraseña de la
> cuenta).

#### Comandos

Abre una terminal (PowerShell o Git Bash), ubícate en la carpeta del proyecto y
ejecuta, en orden:

```
cd C:\Users\pablo\Dropbox\Trabajo\AVEC-CUAM\WEB SITE - EPES CASA DON BOSCO\Web-Pablo>
git init
git config user.name "CasaDonBosco"
git config user.email "pablojbritod@gmail.com"
git add .
git commit -m "Sitio Casa Don Bosco"
git branch -M main
git remote add origin https://github.com/CasaDonBosco/casa-don-bosco.git
git push -u origin main
```

En el `git push` es cuando GitHub pedirá autenticación (navegador, o usuario y token,
según lo descrito arriba). Al terminar, recarga la página del repositorio en la web:
deberías ver `index.html` y las carpetas `assets` y `cursos`.

> El archivo `.gitignore` ya viene en el proyecto, así que `git add .` no subirá
> archivos temporales. El archivo `.nojekyll` (que ayuda a GitHub Pages) también se
> sube automáticamente.

### Opción A — Manual, por la web (alternativa)

1. En la página del repositorio vacío, usa **Add file**, luego **Upload files**.
2. Abre la carpeta del proyecto **`Web-Pablo`** en tu PC.
3. **Muy importante:** arrastra el **contenido** de la carpeta (los archivos y las
   carpetas `assets` y `cursos`), **no** la carpeta `Web-Pablo` en sí. El objetivo es
   que `index.html` quede en la **raíz** del repositorio.
4. Abajo, en **Commit changes**, confirma con el botón **Commit changes**.

---

## Parte 3 — Activar GitHub Pages

1. En el repositorio, entra a la pestaña **Settings** (Configuración).
2. En el menú de la izquierda, haz clic en **Pages**.
3. En **Build and deployment**, en **Source**, elige **Deploy from a branch**.
4. En **Branch**: selecciona **`main`**, carpeta **`/ (root)`**, y haz clic en **Save**.
5. Espera 1 a 3 minutos y recarga: aparecerá un recuadro verde con
   *"Your site is live at…"* y la dirección del sitio.

---

## Parte 4 — Ver el sitio publicado

1. La dirección será: `https://casadonbosco.github.io/casa-don-bosco/`
2. Ábrela en el navegador. Verás la página de Inicio, con el menú, los cursos y las
   imágenes.
3. Si al abrirla ves un error **404** o algo sin estilos, **espera unos minutos** y
   recarga. La primera publicación puede tardar hasta ~10 minutos.

Comprueba: el menú (Inicio, Quiénes Somos, Cursos), las tarjetas de curso, el botón
**"Preinscríbete ¡YA!"** (abre el formulario de Google) y que se vea bien en el teléfono.

---

## Parte 5 — Cómo actualizar el sitio más adelante

Cada vez que cambies un texto o una foto en tu PC, sube los cambios con:

```
cd C:\Users\casal\Claude\Projects\Web-Pablo
git add .
git commit -m "Describe aquí el cambio"
git push
```

En 1–2 minutos el sitio publicado se actualiza solo. (Si prefieres, también puedes
editar archivos directamente en la web de GitHub con el ícono del lápiz y
**Commit changes**.)

---

## Problemas comunes

- **`git push` es rechazado por autenticación:** revisa que usaste el **token** como
  contraseña (no la contraseña de la cuenta), y que el token tiene el permiso `repo`.
- **"remote origin already exists":** ya habías añadido el remoto; usa
  `git push -u origin main` (o corrige el remoto con `git remote set-url origin ...`).
- **Se ve el texto pero sin colores ni tipografía:** casi siempre es esperar unos
  minutos tras activar Pages. Si sigue, revisa que la carpeta `assets` esté en la raíz.
- **Un curso da 404:** verifica que la carpeta `cursos` (con los 10 archivos `.html`)
  se subió completa.
- **Una imagen no aparece:** las fotos actuales son de banco (temporales) y necesitan
  internet; si una no carga, se muestra un bloque azul de respaldo. Se reemplazan fácil
  por fotos reales más adelante.

---

## Alternativa: dirección más corta (opcional)

Si prefieres que la dirección sea `https://casadonbosco.github.io/` (sin
`/casa-don-bosco/` al final), nombra el repositorio exactamente
**`CasaDonBosco.github.io`** en la Parte 1. El resto de pasos es igual. Nota: solo
puede haber **un** sitio de este tipo por cuenta.
