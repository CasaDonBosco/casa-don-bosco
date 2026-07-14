# Casa Don Bosco — Sistema de Diseño
> Derivado del sistema **Organic**, adaptado a la identidad de E.P.E.S Casa Don Bosco Servicios:
> paleta **azul con degradados**, formas redondeadas, tono cálido, familiar y eclesiástico.

## 1. Principios

- **Cálido y familiar**: layouts asimétricos alineados a la izquierda, mucho aire, formas suaves.
- **Redondeado**: radios generosos (16–28px) que crecen hasta píldoras (`border-radius: 999px`) en botones, tags e inputs, y formas circulares/arcos en imágenes.
- **Fotografía lavada**: toda foto de contenido va dentro de `.washed` (desaturada y aclarada) para que se integre al fondo en vez de flotar encima.
- **Azul como voz principal**: azul profundo (acento 1) + azul cielo (acento 2), con degradados en superficies protagonistas (cintas, CTA, footer, botón primario).

## 2. Tokens de color

Definidos en OKLCH sobre una escala de luminosidad compartida (el paso 500 es la base de cada rol).

| Token | Valor | Uso |
| --- | --- | --- |
| `--color-bg` | oklch(96.5% 0.012 250) | Fondo de página (blanco azulado) |
| `--color-surface` | oklch(92.5% 0.025 245) | Fondo de cards, inputs, diálogos |
| `--color-text` | oklch(24% 0.03 258) | Texto principal |
| `--color-accent` | oklch(56% 0.17 258) | Azul profundo — acciones, énfasis |
| `--color-accent-2` | oklch(62% 0.11 225) | Azul cielo — segunda voz |
| `--color-divider` | oklch(85% 0.03 248) | Bordes y reglas |

### Rampas tonales (100–900)

Cada rol tiene rampa `--color-accent-100…900`, `--color-accent-2-100…900`, `--color-neutral-100…900`.

- **100–300**: fondos teñidos, hovers, bordes sutiles.
- **500**: base del rol.
- **600–700**: hover/pressed y texto de tamaño párrafo sobre fondo claro (usa `--color-accent-700`, no el 500, para asegurar contraste).
- **800–900**: superficies oscuras y texto sobre fondos teñidos.

### Degradados de marca

| Token | Composición | Uso |
| --- | --- | --- |
| `--grad-brand` | 120°, accent-600 → accent-400 | Botón primario |
| `--grad-deep` | 135°, accent-800 → accent-500 | Tarjetas protagonistas (Casa Hogar, citas) |
| `--grad-band` | 90°, accent-900 → accent-600 | Cinta superior, CTA |
| `--grad-footer` | 135°, neutral-900 → accent-900 | Footer |

## 3. Tipografía

| Rol | Fuente | Notas |
| --- | --- | --- |
| Títulos | **Caprasimo** 400 (`--font-heading`) | Única voz display; no usar condensadas ni geométricas |
| Cuerpo | **Figtree** 400/600/700 (`--font-body`) | Cuerpo base 15px / 1.55 |

Escala de encabezados: h1 42px · h2 32px · h3 25px · h4 20px · h5 16px · h6 13px (uppercase, tracking .08em).

## 4. Espaciado y radios

- Espaciado: `--space-1` 4.4px · `--space-2` 8.8 · `--space-3` 13.2 · `--space-4` 17.6 · `--space-6` 26.4 · `--space-8` 35.2.
- Radios: `--radius-sm` 8px · `--radius-md` 16px · `--radius-lg` 28px.
- Regla de forma: contenedores → `--radius-lg`; controles pequeños (botones, tags, inputs, seg) → **999px (píldora)**.
- Formas decorativas: arcos en imágenes (`border-radius: 180px 180px 28px 28px`), círculos completos (`border-radius: 50%`).

## 5. Elevación

`--shadow-sm` / `--shadow-md` / `--shadow-lg` (sombras entintadas del azul de marca). Utilidades: `.elev-sm`, `.elev-md`, `.elev-lg`.

## 6. Iconos

Lucide (https://lucide.dev) con `stroke-width: 2.75` para un trazo redondeado y pesado.

## 7. Componentes

| Clase | Qué es |
| --- | --- |
| `.btn` + `.btn-primary` / `.btn-secondary` / `.btn-ghost` / `.btn-icon` / `.btn-block` | Botones; el primario lleva `--grad-brand` |
| `.tag` + `.tag-accent` / `.tag-accent-2` / `.tag-neutral` / `.tag-outline` | Etiquetas teñidas de las rampas |
| `.card` + `.card-kicker` / `.card-title` / `.card-body` / `.card-meta` | Tarjetas de contenido sobre `--color-surface` |
| `.field` + `.input`, `.radio` + `.dot`, `.seg` + `.seg-opt` | Formularios sobre elementos nativos, sin JS |
| `.nav` + `.nav-brand` | Barra de navegación |
| `.table` | Tablas con cabecera y filas tematizadas |
| `.dialog-backdrop` + `.dialog` | Modal en la elevación máxima |
| `.washed` | Envoltorio obligatorio de fotografías |
| `.band-gradient` / `.panel-deep` / `.footer-gradient` | Superficies con degradado de marca |

## 8. Estados e interacción

- **Hover con movimiento**: botones se elevan (−2px + sombra), cards suben (−6px + `--shadow-lg`), fotos hacen zoom 1.05, tags −2px. Transiciones 200–500ms ease.
- **Pressed**: un paso más profundo de la rampa (o `brightness(0.95)` sobre degradado).
- **Focus teclado**: `outline: 2px solid var(--color-accent); outline-offset: 2px` — nunca el anillo azul por defecto del navegador.
- **Selección**: tinte del acento al 30%.
- **Disabled**: opacidad 45%.

## 9. Uso

1. Enlaza `casa-don-bosco.css` en cada página (las fuentes se cargan vía @import).
2. Construye con las clases y tokens; **nunca** hardcodees hex, fuentes o px que ya existan como token.
3. Toda foto dentro de `<div class="washed" style="border-radius:…; overflow:hidden">`.
4. Ver `ejemplo.html` como guía de implementación.

## Qué NO hacer

- Esquinas afiladas o geometría de línea fina.
- Desaturar la paleta a grises: el azul es la identidad.
- Otras display faces distintas de Caprasimo.
- Amontonar elementos: las formas redondas necesitan aire.
- Usar el acento 500 para texto de párrafo (usar 700).
