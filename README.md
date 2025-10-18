# Nexum Ingeniería — Web informativa (HTML/CSS/JS)

Sitio **estático** y **responsive** para presentar a Nexum Ingeniería: servicios, proyectos y contacto. Construido con **HTML5 + CSS3 (Flex/Grid)** y **JavaScript vanilla**, sin frameworks.

---

## Estructura

```
.
├─ index.html                 # Home
├─ pages/
│  ├─ servicios.html          # Subpágina de servicios
│  ├─ proyectos.html          # Subpágina de proyectos (con filtros)
│  └─ contactanos.html        # Subpágina de contacto
├─ css/
│  └─ styles.css
├─ js/
│  └─ app.js
└─ assets/
   ├─ brand/                  # logos, favicons
   ├─ hero/                   # imágenes de cabecera (home/servicios/proyectos/contacto)
   ├─ icons/                  # íconos de servicios
   ├─ logos/                  # logos de clientes
   ├─ iso/                    # sellos ISO
   ├─ certificados/           # certificados (imágenes)
   ├─ brochure/               # PDF del brochure
   └─ proyectos/              # galerías por sector
      ├─ retail/
      ├─ educativo/
      ├─ oficinas/
      ├─ clinicas/
      ├─ inmobiliario/
      ├─ evaluaciones/
      └─ pistas/
```

---

## Funcionalidades destacadas

- **Responsive** con Flexbox + CSS Grid (sin librerías externas).
- **Hero con overlay** configurable por página vía CSS custom property (`--hero-bg`).
- **Sección de Servicios** con tabs y pasos del proceso.
- **Carrusel de clientes** (auto-scroll con pausa al hover/foco).
- **Proyectos**:
  - Búsqueda por texto.
  - Filtros por **sector** y **tipo de servicio** (chips independientes).
  - Paginación por lotes asegurando **filas completas**.
  - Carga inmediata de imágenes visibles para evitar “lazy ghost”.
- **Certificaciones** con imágenes centradas y tamaños uniformes.
- **Contacto**:
  - Formulario validado en cliente.
  - Checkbox de consentimiento corregido (no estira ancho).
  - Scroll al enviar para mostrar el estado.
- **CTA del brochure** que abre el PDF en **nueva pestaña**.
- **Favicon** con el logo de marca.

---

## Cómo probar

No requiere build ni servidor. Abre **`index.html`** en tu navegador.

> Consejo: si usas VS Code, la extensión *Live Server* ayuda con recarga automática.

---

## Gestión de assets

- **Héroes**:  
  - `assets/hero/obra-en-progreso-1920x1080.jpg` (Home)  
  - `assets/hero/planos-obra-1920x640.jpg` (Servicios)  
  - `assets/hero/proyectos-1920x640.jpg` (Proyectos)  
  - `assets/hero/contacto-1920x640.jpg` (Contáctanos)  
  Sugerencia: JPG 1920×640/1080, 200–350 KB, foco centrado/derecha.

- **Proyectos**: imágenes **1200×800** (ratio 3:2), nombradas por proyecto y ubicadas en la subcarpeta del **sector** correspondiente.

- **Favicon**: en `assets/brand/`. En `<head>`:
  ```html
  <link rel="icon" href="assets/brand/logo-nexum.png" type="image/png">
  ```
  (en subpáginas usar `../assets/brand/...`)

---

## Cómo añadir un proyecto

1. Coloca la imagen (1200×800) en la subcarpeta de sector:  
   `assets/proyectos/<sector>/mi-proyecto-1200x800.jpg`

2. En `pages/proyectos.html`, dentro de la **gallery** (`data-gallery="proyectos"`), añade una tarjeta:

```html
<article class="card project-card"
         data-sector="Retail"
         data-servicio="Gerencia/Supervisión"> <!-- Tipo de servicio -->
  <img src="../assets/proyectos/retail/mi-proyecto-1200x800.jpg"
       alt="Mi Proyecto — descripción corta" loading="lazy" decoding="async">
  <div class="project-body">
    <h3>Mi Proyecto — Subtítulo</h3>
    <p class="meta">Cliente: Nombre</p>
    <p class="meta">Monto: S/ 1,000,000</p>
    <p class="meta">Área: 1,200 m²</p>
  </div>
</article>
```

3. Si el proyecto no encaja claramente en un servicio, asígnalo al bucket con menos proyectos para balancear los filtros.

> Los filtros funcionan leyendo `data-sector` y `data-servicio`. La búsqueda recorre el texto de la tarjeta.

---

## Personalización rápida

- **Colores / tipografías / espacios**: variables en `:root` dentro de `css/styles.css`.
- **Logo del header**: `assets/brand/logo-nexum.*`  
  Tamaño controlado por `--logo-size` en CSS.
- **Overlay del hero**: ajusta opacidades en:
  ```css
  .hero, .page-hero{
    background: linear-gradient(180deg, rgb(0 0 0 / 15%), rgb(0 0 0 / 6%)), var(--hero-bg) center/cover no-repeat;
  }
  ```

---

## Accesibilidad y UX

- Navegación por teclado en tabs y acordeón.
- `aria-label`, `role="status"` (mensajes) y `aria-live` en interacciones clave.
- Contraste asegurado en botones del hero (ghost con fondo claro).
- Imágenes con `alt` descriptivo.

---

## Estructura de JS (resumen)

- **Nav móvil**
- **Tabs de Servicios**
- **Acordeón de Política**
- **Carrusel de Clientes**
- **Proyectos**: filtros, paginado por filas completas y carga de imágenes visibles
- **Formulario**: validación básica y scroll al enviar
- **Reveal on Scroll**

Todo vive en **`js/app.js`**, separado por bloques con un comentario de título.

---

## Despliegue

- **GitHub Pages**: sube a `main` y activa Pages desde *Settings → Pages*.
- Cualquier hosting estático (Netlify, Vercel, S3, etc.) funciona sin cambios.

---

## Notas

- Las imágenes y logos de terceros deben usarse respetando sus licencias.
- Los nombres de archivos en `assets/` están alineados con el HTML/JS; respétalos para evitar rutas rotas.

---

## Licencia

Proyecto de **sitio estático** para Nexum Ingeniería. El contenido y la marca pertenecen a sus respectivos titulares. El código fuente puede reutilizarse internamente citando la procedencia.
