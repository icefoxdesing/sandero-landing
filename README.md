# Sandero Expresión 2019 — Landing de venta

Landing page estática para la venta particular de un Renault Sandero Expresión 2019 con 85.000 km, papeles al día, ubicado en Patagonia (Argentina).

**🌐 En vivo:** [https://icefoxdesing.github.io/sandero-landing/](https://icefoxdesing.github.io/sandero-landing/)



---

## ✨ Qué incluye

- **Slider hero** con auto-play (4 s) entre vista frontal y vista 3/4 con cordillera.
- **Slider lateral** en sección Historia entre las dos tomas laterales.
- **Galería** con lightbox: click en cualquier foto para verla en grande, navegación con teclado y flechas.
- **Banda de precio** con disclaimer de fecha + CTA a WhatsApp para precio del día.
- **FAQ** acordeón con las 4 preguntas más comunes (permuta, financiación, test drive, transferencia).
- **Botón flotante de WhatsApp** siempre visible.
- **Botón "volver arriba"** que aparece al scrollear.
- **Menú con scrollspy**: el link de la sección activa se resalta en el nav.
- **Menú mobile** full-screen con hamburguesa animada.
- **Compartir página** desde el nav, el CTA o el menú mobile (Web Share API + clipboard fallback).
- **Open Graph** para previews lindas al compartir en WhatsApp/Facebook.
- **Schema.org Vehicle** para mejor indexación en Google.

---

## 📁 Estructura

```
sandero-landing/
├── index.html              ← todo el código en un solo archivo (HTML + CSS + JS embebidos)
├── README.md               ← este archivo
└── images/
    ├── hero-frontal.jpg        — slide 1 del hero
    ├── hero-cordillera.jpg     — slide 2 del hero
    ├── lateral-derecho.jpg     — slide 1 de Historia
    ├── lateral-izquierdo.jpg   — slide 2 de Historia
    ├── frente-grande.jpg       — galería
    ├── interior.jpg            — galería
    ├── trasera.jpg             — galería
    └── motor.jpg               — galería
```

> ⚠️ Los nombres de archivo deben respetarse exactamente (minúsculas, sin acentos, sin espacios). El HTML los referencia tal cual.

---

## 🛠 Cómo modificar cosas comunes

Toda la página vive en `index.html`. No hay build, no hay dependencias. Editás el archivo, hacés commit y se actualiza.

### Cambiar el precio

Buscá en `index.html` la sección `<!-- PRICE BAND -->` y editá:

```html
<div class="price-amount">
  <span class="currency">$</span>14.000.000   <!-- ← acá -->
</div>
```

Y la fecha del disclaimer un poco más abajo:

```html
<p class="price-disclaimer">
  Precio orientativo al 26/04/2026. ...   <!-- ← acá -->
</p>
```

También conviene actualizar el precio en el bloque `<script type="application/ld+json">` del `<head>` para mantener consistencia con Google:

```json
"price": "14000000"
```

### Reemplazar una foto

1. Pegá la foto nueva en `images/` con el **mismo nombre** que reemplaza.
2. Commit. Listo.

Si querés cambiar el nombre de archivo, también tenés que actualizar la referencia dentro de `index.html` (buscar el `src="images/…"` correspondiente).

### Editar una pregunta del FAQ

Buscá `<!-- FAQ -->` en `index.html`. Cada pregunta es un bloque así:

```html
<div class="faq-item reveal">
  <button class="faq-question" aria-expanded="false">
    <span>¿Aceptás permuta?</span>     <!-- ← pregunta -->
    ...
  </button>
  <div class="faq-answer">
    <div class="faq-answer-inner">
      No, esta vez vendo solo. ...      <!-- ← respuesta -->
    </div>
  </div>
</div>
```

Para agregar una pregunta nueva, copiás un bloque entero y lo pegás dentro de `<div class="faq-list">`.

### Cambiar el número de WhatsApp

El número aparece en varios lugares (nav, FAB, banda de precio, CTA, menú mobile). Para reemplazarlo en todos a la vez, buscá y reemplazá:

```
5492994712095   →  tu nuevo número (formato internacional sin + ni espacios)
```

El formato es `54` (Argentina) + `9` (móvil) + característica + número.

### Cambiar el texto del hero

Buscá `<!-- HERO -->` y editá:

```html
<h1 class="display">
  El auto que <br>
  ya conoce <br>
  la <em>ruta.</em>
</h1>
```

### Marcar el auto como vendido

Cuando se venda, podés:

1. **Opción rápida:** agregar arriba del nav un banner "VENDIDO".
2. **Opción más limpia:** cambiar el `<title>` y el meta `og:title` a *"VENDIDO — Sandero 2019"*, y modificar el hero h1 a *"Vendido. Gracias a todos los que consultaron."*.

---

## 🚀 Cómo correr localmente

No requiere nada. Doble click en `index.html` y se abre en el navegador.

Para desarrollo más serio (con live-reload), si tenés Node.js instalado:

```bash
npx serve .
```

O con Python:

```bash
python3 -m http.server 8000
```

Y abrís `http://localhost:8000`.

---

## 🌐 Cómo desplegar a GitHub Pages

1. Crear repo público en GitHub con nombre `sandero-landing`.
2. Subir `index.html`, `README.md` y la carpeta `images/`.
3. **Settings → Pages → Source: Deploy from a branch → main → / (root) → Save**.
4. Esperar 1–2 minutos. La URL queda en `https://TU-USUARIO.github.io/sandero-landing/`.

Cualquier commit posterior a la branch `main` redespliega automáticamente.

---

## 🎨 Stack técnico

- **HTML semántico** sin frameworks
- **CSS** con variables, grid, flexbox y `aspect-ratio`
- **JavaScript** vanilla (sin librerías)
- **Tipografías:** [Fraunces](https://fonts.google.com/specimen/Fraunces) (display) + [DM Sans](https://fonts.google.com/specimen/DM+Sans) (body), servidas desde Google Fonts
- **Iconos:** SVG inline
- **Sin build step.** Todo el código en un único archivo de ~70 KB

### Decisiones de diseño

- Paleta inspirada en la Patagonia: papel crema, carbón profundo, dorado patagónico, terracota, gris cielo.
- Tipografía editorial-aventurera (Fraunces variable con cursivas en acentos).
- Texturas de grano sutiles vía SVG embebido en CSS.
- Animaciones suaves con `IntersectionObserver` para reveal on scroll.

---

## 📜 Licencia

Sin licencia. Todos los derechos reservados.

El código es público para que GitHub Pages funcione, pero no se autoriza su reutilización ni redistribución. Las fotografías son propiedad del autor.

Si te interesa usar esta plantilla para tu propia venta, abrí un *issue* y lo conversamos.

---

## 📞 Contacto

Para consultas sobre el auto:
- **WhatsApp:** [+54 9 299 471 2095](https://wa.me/5492994712095)
- **Alternativo:** +54 9 299 553 0612

Para consultas sobre el código de esta landing:
- Abrir un issue en este mismo repositorio.

---

*Hecho con cuidado, en Patagonia, Argentina.*
