---
name: Diseño fluido y media queries mobile-first
overview: Aplicar diseño fluido y media queries con enfoque mobile-first al portfolio, haciendo que sea completamente responsive y usando técnicas modernas de CSS como clamp(), minmax(), y unidades relativas.
todos:
  - id: "1"
    content: Convertir tipografía a unidades fluidas usando clamp() y rem - aplicar a h1, h2, h3, h4, hero__title, hero__subtitle, y otros elementos de texto
    status: pending
  - id: "2"
    content: "Hacer contenedores fluidos - cambiar max-width fijos por width: min() y padding relativo usando clamp() o rem"
    status: pending
  - id: "3"
    content: "Crear grid responsive para proyectos - mobile: 1 columna, tablet: 2 columnas, desktop: 3 columnas usando minmax()"
    status: pending
  - id: "4"
    content: "Hacer navegación responsive mobile-first - móvil: vertical/apilada, tablet/desktop: horizontal"
    status: pending
  - id: "5"
    content: Ajustar hero stats para móvil - usar flex-wrap y espaciado responsive
    status: pending
  - id: "6"
    content: "Hacer values grid responsive - móvil: 1 columna, tablet+: 2 columnas"
    status: pending
  - id: "7"
    content: Mejorar contact methods responsive - ajustar anchos y espaciado para diferentes pantallas
    status: pending
  - id: "8"
    content: "Agregar media queries mobile-first al final del CSS - @media (min-width: 768px) y @media (min-width: 1024px)"
    status: pending
  - id: "9"
    content: "Asegurar que imágenes y elementos visuales sean fluidos - max-width: 100% y tamaños mínimos apropiados"
    status: pending
  - id: "10"
    content: Revisar y ajustar espaciados, márgenes y padding para que sean consistentes y fluidos en todas las secciones
    status: pending
isProject: false
---

# Plan: Aplicar Diseño Fluido y Media Queries Mobile-First

## Contexto

El archivo `clase_09_reto_fundamentos/index.html` tiene un portfolio con estilos básicos que no es responsive. Necesitas aplicar:

- **Diseño fluido**: usar unidades relativas, `clamp()`, `minmax()`, porcentajes
- **Media queries**: con enfoque mobile-first (estilos base para móvil, luego mejoras para tablet/desktop)
- **Responsive design**: que se adapte a diferentes tamaños de pantalla

## Conceptos Clave

### Mobile First

- Los estilos base se escriben para móvil (pantallas pequeñas)
- Luego se agregan `@media (min-width: ...)` para pantallas más grandes
- Breakpoints comunes: 768px (tablet), 1024px (desktop)

### Diseño Fluido

- Usar `clamp(min, preferred, max)` para tipografía que escala suavemente
- Usar `minmax()` en Grid para columnas que se adaptan automáticamente
- Usar porcentajes y unidades relativas (`rem`, `em`, `vw`, `vh`) en lugar de píxeles fijos

## Archivos a Modificar

- `clase_09_reto_fundamentos/styles.css` - Aplicar diseño fluido y media queries

## Tareas Específicas

### 1. Tipografía Fluida

- Convertir tamaños de fuente fijos (`px`) a `clamp()` o `rem`
- Ejemplo: `font-size: 52px` → `font-size: clamp(2rem, 5vw, 3.25rem)`
- Aplicar a: `h1`, `h2`, `h3`, `h4`, `.hero__title`, `.hero__subtitle`, etc.

### 2. Contenedores y Espaciado Fluido

- Convertir `max-width` fijos a valores más flexibles
- Usar `width: 90%` o `width: min(90%, 1200px)` en lugar de solo `max-width`
- Aplicar padding relativo usando `rem` o porcentajes

### 3. Grid de Proyectos Responsive

- Actualmente los proyectos están apilados sin grid
- Crear grid fluido con `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))`
- En móvil: 1 columna, tablet: 2 columnas, desktop: 3 columnas

### 4. Navegación Mobile-First

- En móvil: menú vertical o hamburguesa
- En tablet/desktop: menú horizontal
- Usar `flex-direction: column` en móvil, `row` en desktop

### 5. Hero Stats Responsive

- En móvil: apilar verticalmente o en una sola fila pequeña
- En desktop: mantener horizontal con espaciado adecuado
- Usar `flex-wrap: wrap` y ajustar márgenes

### 6. Values Grid Responsive

- Actualmente tiene `grid-template-columns: 1fr 1fr` (siempre 2 columnas)
- Mobile-first: 1 columna en móvil, 2 en tablet, mantener 2 en desktop
- Usar `grid-template-columns: 1fr` por defecto, luego `repeat(2, 1fr)` en media query

### 7. Contact Methods Responsive

- Ya tiene `flex-wrap: wrap` pero necesita mejor espaciado
- Ajustar anchos para que se vean bien en móvil (100% o casi) y desktop

### 8. Media Queries Mobile-First

Agregar media queries al final del archivo CSS:

```css
/* Tablet: 768px en adelante */
@media (min-width: 768px) {
  /* Ajustes para tablet */
}

/* Desktop: 1024px en adelante */
@media (min-width: 1024px) {
  /* Ajustes para desktop */
}
```

### 9. Imágenes y Elementos Visuales

- Asegurar que todos los elementos con ancho fijo usen `max-width: 100%`
- Botones y elementos interactivos con tamaños mínimos apropiados

### 10. Testing Visual

- Verificar que el sitio se vea bien en:
  - Móvil (320px - 767px)
  - Tablet (768px - 1023px)
  - Desktop (1024px+)

## Ejemplos de Cambios Específicos

### Tipografía Fluida

```css
/* Antes */
h1 { font-size: 52px; }

/* Después */
h1 { font-size: clamp(2rem, 5vw, 3.25rem); }
```

### Grid Fluido

```css
/* Antes */
.projects__grid { /* sin grid definido */ }

/* Después */
.projects__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}

@media (min-width: 768px) {
  .projects__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .projects__grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

### Contenedores Fluidos

```css
/* Antes */
.header__container {
  max-width: 1200px;
  padding: 0 20px;
}

/* Después */
.header__container {
  width: min(90%, 1200px);
  margin: 0 auto;
  padding: 0 clamp(1rem, 4vw, 2rem);
}
```

