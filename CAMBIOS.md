# Historial de Cambios - README zBleend

## Paleta de colores

- Fondo oscuro: `#0a0a0a` → `#111111`
- Texto principal (hueso): `#e8d5b7`
- Acento dorado: `#c9a87c`
- Gris medio: `#555555`
- Borde sutil: `#1a1a1a`, `#222222`

---

## 📋 Planificación Inicial (SVGs Separados)

### `assets/banner.svg` (eliminado)

- Título: "Cristóbal" en color hueso `#e8d5b7`
- Subtítulo: "CODE · FULLSTACK DEVELOPER · MUSIC" en gris `#555555`
- Decoración con caracteres japoneses: 力, 美, 刀
- Líneas decorativas horizontales en `#c9a87c` con opacidad baja
- Fondo oscuro con degradado sutil

### `assets/sobre-mi.svg` (eliminado)

- Terminal minimalista sobre fondo oscuro
- Colores: dorado `#c9a87c` para prompts, hueso `#e8d5b7` para texto
- Caracteres decorativos 力 y 美 en esquinas
- Animación de typing rápida y limpia
- Contenido: [ESTUDIANTE], [PRODUCTOR], [ENFOQUE], [CONTACTO]

### `assets/stack.svg` (eliminado)

- Iconos SVG minimalistas hand-crafted para cada tecnología
- Tecnologías: Java, Python, JavaScript, TypeScript, React, Vue, SQL, Docker, Git, Linux
- Fondo `#0a0a0a` con borde `#1a1a1a`
- Decoración japonesa 力

### `README.md`

- Banner con SVG actualizado
- Typing SVG animado con color dorado `#c9a87c`
- Badges de redes (LinkedIn, Gmail) en estilo flat-square oscuro
- Tarjetas de proyectos con CSS inline (fondo `#0a0a0a`, borde `#1a1a1a`, border-radius 4px)
- Links de proyecto con estilo `→ Ver Código` en dorado
- Badges de tech con logos por proyecto
- Separadores con `══════════`
- Footer con `力 · 美 · 刀` y `2026 · Cristóbal`

---

## 🔧 Especificaciones Técnicas (de CAMBIOS.md original)

### 1. Adaptabilidad de Fondo (Modo Claro/Oscuro)

- **Fondo Adaptable:** Configura el fondo del SVG utilizando variables multimedia (`@media (prefers-color-scheme: dark)`) en la etiqueta `<style>` interna.
- **Alternativa Segura:** Si prefieres un fondo fijo, usa un degradado oscuro que resalte tanto en el feed blanco como en el negro de GitHub, asegurando que los iconos del stack mantengan su contraste.

### 2. Grid Visual del Stack (Estructura en Bloques)

- **Distribución:** En lugar de una lista plana, organiza el stack en bloques o "cajas" visuales ordenadas de arriba hacia abajo (Fronend -> Backend -> Lenguajes -> Herramientas).
- **Prevención de Deformidad:** Cada icono vectorial debe estar encapsulado en su propio `<g>` con coordenadas `x` e `y` fijas.
- **Iconos Integrados:** Incrustar los paths vectoriales directamente (inline). No usar links externos.

### 3. Kanjis y Arte ASCII en GitHub

- **Fuentes Seguras:** Para los Kanjis/Kanas utiliza la pila del sistema: `font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;`.
- **Katanas ASCII sin Romperse:**
  - Usa estrictamente una fuente monoespaciada nativa (`font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, monospace;`).
  - Utiliza un elemento `<text>` con múltiples etiquetas `<tspan x="coordenada_fija" dy="1.2em">` (una por cada línea del ASCII).

---

## ✅ Implementación Realizada (SVG Unificado)

### Cambio de Arquitectura: 3 SVGs → 1 SVG Unificado

**Fecha:** 2026-09-01

**Decisión:** Combinar `banner.svg`, `sobre-mi.svg` y `stack.svg` en un solo archivo `assets/main.svg` para mantener un fondo completo y estético cohesivo.

### Archivos Eliminados

- `assets/banner.svg`
- `assets/sobre-mi.svg`
- `assets/stack.svg`

### Archivo Creado: `assets/main.svg`

**Dimensiones:** `viewBox="0 0 1200 900"`

#### Sección 1: Banner (y: 0 → 300)

- Katana ASCII art de fondo (`opacity: 0.25`, `#888888`, fuente monoespaciada segura)
- Kanjis 力 美 刀 decorativos con fuente del sistema
- Nombre "Cristóbal" en `#e8d5b7` (font-size: 72)
- Subtítulo "CODE · FULLSTACK DEVELOPER · MUSIC" en `#555555` (font-size: 18)
- Líneas decorativas doradas `#c9a87c` con opacidad baja

#### Sección 2: Sobre mí / Terminal (y: 320 → 620)

- Terminal con barra de título (dots rojo/amarillo/verde)
- Animaciones de typing secuenciales:
  - `whoami` → `[ESTUDIANTE] Analista Programador · Duoc UC`
  - `[PRODUCTOR] Musical · IP ARCOS`
  - `[ENFOQUE] frontend, backend, bd, código limpio`
  - `[CONTACTO] juancrichile@gmail.com`
- Cursor parpadeante
- Kanjis 力 y 美 decorativos en esquinas

#### Sección 3: Stack (y: 640 → 880)

**17 tecnologías en fila horizontal:**

```
HTML · CSS · JS · React · Astro · Vue | Java · Spring · Python | GitHub · Kotlin | VSCode · AndroidStudio · IntelliJ | AWS · Ableton · Bash
```

**Iconos SVG minimalistas:**

| Tecnología | Diseño |
|------------|--------|
| HTML | Tag `<>` |
| CSS | Llaves `{ }` |
| JS | `JS` bold |
| React | Átomo (3 elipses) |
| Astro | Constelación/estrella |
| Vue | Escudo |
| Java | Taza café |
| Spring | Hoja de trébol |
| Python | `Py` |
| GitHub | Terminal/gato |
| Kotlin | `K` angular |
| VSCode | `</>` en cuadro |
| AndroidStudio | Robot/android |
| IntelliJ | `IJ` monograma |
| AWS | Nube |
| Ableton | Rectángulos del logo |
| Bash | `$_` prompt |

### Cambios en `README.md`

- **Antes:** 3 referencias SVG separadas (banner, typing SVG externo, sobre-mi, stack)
- **Después:** 1 sola referencia `assets/main.svg`
- **Footer:** Colores cambiados de `#333333`/`#222222` a `#666666` para visibilidad en dark mode

### Bloque `<style>` Global

```css
.font-sans { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; }
.font-mono { font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, monospace; }

@media (prefers-color-scheme: dark) {
  .bg-rect { fill: #0a0a0a; }
}
@media (prefers-color-scheme: light) {
  .bg-rect { fill: #f5f0eb; }
  .fill-bone { fill: #2a1f14; }
  .fill-gold { fill: #a07840; }
  .fill-gray { fill: #666666; }
}
```

### Stack Original vs Nuevo

| Original (CAMBIOS.md) | Nuevo (Implementado) |
|-----------------------|----------------------|
| Java, Python, JavaScript, TypeScript, React, Vue, SQL, Docker, Git, Linux | HTML, CSS, JS, React, Astro, Vue, Java, Spring, Python, GitHub, Kotlin, VSCode, AndroidStudio, IntelliJ, AWS, Ableton, Bash |
| Fila plana sin categorías | Fila horizontal con separadores verticales por categoría |
| 10 tecnologías | 17 tecnologías |

### Limitaciones Conocidas

- GitHub **no soporta** `@media` queries en SVGs embebidos en Markdown (los SVGs se renderizan como `<img>` sin soporte CSS externo)
- Las fuentes externas (Noto Sans JP, JetBrains Mono) fueron reemplazadas por fuentes del sistema para garantizar compatibilidad
