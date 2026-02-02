# 📚 DOCUMENTACIÓN TÉCNICA - PÁGINA WEB SERVITIC

## 📖 Índice

1. [Descripción General](#-descripción-general)
2. [Estructura HTML](#️-estructura-html)
3. [Estilos CSS](#-estilos-css)
4. [Guía de Mantenimiento](#-guía-de-mantenimiento)
5. [Ejercicios de Ampliación](#-ejercicios-de-ampliación)
6. [Glosario de Términos](#-glosario-de-términos)
7. [Recursos Adicionales](#-recursos-adicionales)

---

## 🎯 Descripción General

### ¿Qué es este proyecto?

Una página web corporativa profesional para **SERVITIC**, empresa de servicios tecnológicos y mantenimiento informático. La web incluye presentación de servicios, información corporativa y formulario de contacto.

### Tecnologías utilizadas

- **HTML5**: Estructura semántica del contenido
- **CSS3**: Estilos visuales y diseño responsive
- **JavaScript**: (Opcional para futuras mejoras de interactividad)

### Características principales

- ✅ Diseño moderno con gradientes
- ✅ Navegación sticky (se mantiene visible al hacer scroll)
- ✅ Diseño responsive (adaptable a móviles y tablets)
- ✅ Secciones bien definidas (Servicios, Quiénes Somos, Contacto)
- ✅ Formulario de contacto validado con HTML5
- ✅ Grid responsive automático para tarjetas de servicios
- ✅ Footer completo con información legal

---

## 🏗️ Estructura HTML

### Anatomía del documento

```
<!DOCTYPE html>
└── <html lang="es">
    ├── <head>
    │   ├── <meta charset="UTF-8">
    │   ├── <meta name="viewport">
    │   ├── <title>
    │   └── <style>
    └── <body>
        ├── <header>
        │   └── <div class="container">
        │       └── <div class="header-content">
        │           ├── <div class="logo">
        │           └── <nav>
        ├── <section class="hero">
        ├── <section id="servicios">
        │   └── <div class="servicios-grid">
        │       └── <div class="servicio-card"> × 6
        ├── <section id="quienes-somos">
        │   └── <div class="about-content">
        ├── <section id="contacto">
        │   └── <form class="contacto-form">
        └── <footer>
            └── <div class="footer-content">
```

### Elementos HTML utilizados

#### 1. DOCTYPE y HTML

```html
<!DOCTYPE html>
<html lang="es">
```

**Propósito**: Declara el documento como HTML5 y define el idioma español.  
**Importancia**: Necesario para la correcta interpretación del navegador y SEO.  
**Alternativas**: `lang="en"` para inglés, `lang="fr"` para francés.

#### 2. Meta Tags

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- **charset="UTF-8"**: Permite usar caracteres especiales (ñ, acentos, símbolos).
- **viewport**: Hace la página responsive en dispositivos móviles.

**Sin viewport**, la página se vería muy pequeña en móviles (zoom alejado).

#### 3. Header Semántico

```html
<header>
    <div class="container">
        <div class="header-content">
            <div class="logo">SERVITIC</div>
            <nav>
                <ul>
                    <li><a href="#servicios">Servicios</a></li>
                </ul>
            </nav>
        </div>
    </div>
</header>
```

**Etiquetas semánticas usadas**:
- `<header>`: Identifica la cabecera (mejor que `<div>`)
- `<nav>`: Identifica la navegación
- `<ul>` y `<li>`: Lista de enlaces del menú

**Por qué semánticas**: Mejoran SEO y accesibilidad.

#### 4. Secciones de Contenido

```html
<section id="servicios">
    <div class="container">
        <h2>Nuestros Servicios</h2>
        <div class="servicios-grid">
            <div class="servicio-card">
                <h3>Título del servicio</h3>
                <p>Descripción</p>
            </div>
        </div>
    </div>
</section>
```

**IDs vs Classes**:
- `id="servicios"`: Único, para enlaces ancla (`<a href="#servicios">`)
- `class="container"`: Reutilizable en toda la página

#### 5. Formulario de Contacto

```html
<form class="contacto-form">
    <div class="form-group">
        <label for="nombre">Nombre completo</label>
        <input type="text" id="nombre" name="nombre" required>
    </div>
    <button type="submit" class="btn-submit">Enviar Mensaje</button>
</form>
```

**Elementos clave**:
- `<label for="nombre">`: Conecta con `id="nombre"` (accesibilidad)
- `type="email"`: Valida formato de email automáticamente
- `type="tel"`: Teclado numérico en móviles
- `required`: Validación HTML5 (campo obligatorio)
- `<textarea>`: Campo multilínea para mensajes largos

**Alternativas de validación**:
```html
<!-- Limitar longitud -->
<input type="text" maxlength="50">

<!-- Patrón personalizado (9 dígitos) -->
<input type="tel" pattern="[0-9]{9}">

<!-- Valor mínimo/máximo -->
<input type="number" min="18" max="99">
```

#### 6. Footer con Grid

```html
<footer>
    <div class="container">
        <div class="footer-content">
            <div class="footer-section"><!-- Columna 1 --></div>
            <div class="footer-section"><!-- Columna 2 --></div>
            <div class="footer-section"><!-- Columna 3 --></div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2026 SERVITIC - Todos los derechos reservados</p>
        </div>
    </div>
</footer>
```

**Entidades HTML útiles**:
- `&copy;` → ©
- `&reg;` → ®
- `&trade;` → ™
- `&nbsp;` → Espacio no separable
- `&lt;` → <
- `&gt;` → >

---

## 🎨 Estilos CSS

### Conceptos CSS utilizados

#### 1. Reset Global

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**Propósito**: Elimina estilos predeterminados del navegador inconsistentes.

**box-sizing: border-box explicado**:

```
Sin box-sizing (por defecto):
width: 300px + padding: 20px + border: 2px = 322px total ❌

Con box-sizing: border-box:
width: 300px (incluye padding y border) = 300px total ✅
```

**Ejercicio**: Elimina `box-sizing: border-box` y observa cómo los elementos se expanden.

#### 2. Flexbox para Layouts

```css
.header-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
```

**Propiedades de Flexbox**:

| Propiedad | Valores | Efecto |
|-----------|---------|--------|
| `display` | `flex` | Activa Flexbox |
| `flex-direction` | `row`, `column` | Dirección (horizontal/vertical) |
| `justify-content` | `center`, `space-between`, `flex-start`, `flex-end` | Alineación horizontal |
| `align-items` | `center`, `flex-start`, `flex-end`, `stretch` | Alineación vertical |
| `gap` | `2rem`, `20px` | Espacio entre elementos |

**Ejemplos prácticos**:

```css
/* Centrar perfecto horizontal y vertical */
.contenedor {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

/* Elementos en columna con espacio */
.menu {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

/* Distribuir espacio equitativamente */
.footer-content {
    display: flex;
    justify-content: space-evenly;
}
```

#### 3. CSS Grid Responsive Automático

```css
.servicios-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
}
```

**Esta línea es MÁGICA** 🪄

**Desglose**:
- `display: grid`: Activa CSS Grid
- `repeat()`: Repite el patrón de columnas
- `auto-fit`: Crea tantas columnas como quepan automáticamente
- `minmax(280px, 1fr)`: Mínimo 280px, máximo 1 fracción del espacio
- `1fr`: "1 fracción" - divide el espacio equitativamente

**Resultado**:
- **Pantalla grande** (>1200px): 3 columnas
- **Tablet** (768px-1199px): 2 columnas
- **Móvil** (<768px): 1 columna

**Alternativas**:

```css
/* 3 columnas fijas (no responsive) */
grid-template-columns: repeat(3, 1fr);

/* Columnas de ancho fijo */
grid-template-columns: repeat(auto-fit, 300px);

/* Mezcla de anchos */
grid-template-columns: 200px 1fr 2fr;
```

#### 4. Gradientes Lineales

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

**Sintaxis**:
```css
linear-gradient(ángulo, color1 posición1, color2 posición2, ...)
```

**Ángulos comunes**:
- `0deg` o `to top`: ↑ Vertical hacia arriba
- `90deg` o `to right`: → Horizontal derecha
- `135deg`: ↗ Diagonal
- `180deg` o `to bottom`: ↓ Vertical hacia abajo

**Ejemplos creativos**:

```css
/* Horizontal simple */
background: linear-gradient(90deg, red, blue);

/* Múltiples colores */
background: linear-gradient(45deg, red 0%, yellow 50%, green 100%);

/* Gradiente sutil */
background: linear-gradient(180deg, #f8f9fa 0%, #ffffff 100%);

/* Gradiente radial (circular) */
background: radial-gradient(circle, white, black);

/* Gradiente cónico */
background: conic-gradient(red, yellow, green, blue, red);
```

**Herramientas recomendadas**:
- [cssgradient.io](https://cssgradient.io/) - Generador visual
- [uigradients.com](https://uigradients.com/) - Gradientes prediseñados

#### 5. Sombras (box-shadow)

```css
box-shadow: 0 5px 15px rgba(0,0,0,0.1);
```

**Sintaxis**:
```css
box-shadow: horizontal vertical difuminado expansión color;
```

**Ejemplos**:

```css
/* Sombra suave */
box-shadow: 0 2px 4px rgba(0,0,0,0.1);

/* Sombra pronunciada */
box-shadow: 0 10px 30px rgba(0,0,0,0.3);

/* Sombra interna (efecto hundido) */
box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);

/* Múltiples sombras */
box-shadow: 
    0 5px 15px rgba(0,0,0,0.1),
    inset 0 1px 0 rgba(255,255,255,0.1);

/* Sombra de color */
box-shadow: 0 4px 10px rgba(102, 126, 234, 0.3);
```

**Truco para elevación**:
```css
.tarjeta {
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    transition: box-shadow 0.3s;
}

.tarjeta:hover {
    box-shadow: 0 8px 20px rgba(0,0,0,0.2);
}
```

#### 6. Transiciones

```css
.servicio-card {
    transition: transform 0.3s;
}

.servicio-card:hover {
    transform: translateY(-5px);
}
```

**Sintaxis**:
```css
transition: propiedad duración función-de-tiempo retraso;
```

**Ejemplos**:

```css
/* Transición simple */
transition: all 0.3s;

/* Propiedades específicas */
transition: transform 0.3s, opacity 0.5s;

/* Con función de aceleración */
transition: transform 0.3s ease-in-out;

/* Con retraso */
transition: opacity 0.3s 0.1s;
```

**Funciones de tiempo**:
- `ease`: Lento-rápido-lento (por defecto)
- `linear`: Velocidad constante
- `ease-in`: Empieza lento
- `ease-out`: Termina lento
- `ease-in-out`: Lento al inicio y al final
- `cubic-bezier(0.68, -0.55, 0.265, 1.55)`: Personalizado

**Propiedades animables comunes**:
```css
/* Transformaciones */
transform: translateX(100px);
transform: translateY(-10px);
transform: scale(1.1);
transform: rotate(45deg);

/* Visuales */
opacity: 0.5;
background-color: blue;
color: red;

/* Dimensiones */
width: 200px;
height: 300px;
padding: 20px;
```

#### 7. Pseudo-clases

```css
nav a:hover {
    opacity: 0.8;
    background: rgba(255,255,255,0.1);
}

input:focus {
    border-color: #667eea;
}
```

**Pseudo-clases comunes**:

| Pseudo-clase | Cuándo se aplica | Ejemplo de uso |
|--------------|------------------|----------------|
| `:hover` | Al pasar el mouse | Efecto de botones |
| `:focus` | Al hacer clic/seleccionar | Inputs activos |
| `:active` | Al presionar | Botón presionado |
| `:visited` | Enlaces visitados | Cambiar color |
| `:first-child` | Primer hijo | Primera tarjeta |
| `:last-child` | Último hijo | Última tarjeta |
| `:nth-child(n)` | Hijo número n | Cada 2 elementos |
| `:disabled` | Elemento deshabilitado | Input bloqueado |
| `:checked` | Checkbox marcado | Checkbox activo |

**Ejemplos prácticos**:

```css
/* Alternar colores de filas */
tr:nth-child(odd) {
    background: #f0f0f0;
}

tr:nth-child(even) {
    background: white;
}

/* Primer y último elemento especiales */
.menu li:first-child {
    border-top-left-radius: 10px;
}

.menu li:last-child {
    border-bottom-right-radius: 10px;
}

/* No aplicar margen al último */
.tarjeta:not(:last-child) {
    margin-bottom: 20px;
}

/* Estados de enlace */
a:link { color: blue; }      /* No visitado */
a:visited { color: purple; } /* Visitado */
a:hover { color: red; }      /* Mouse encima */
a:active { color: orange; }  /* Presionado */
```

#### 8. Media Queries (Responsive)

```css
@media (max-width: 768px) {
    .header-content {
        flex-direction: column;
    }
    
    .hero h1 {
        font-size: 2rem;
    }
}
```

**Breakpoints estándar**:

| Dispositivo | Ancho | Media Query |
|-------------|-------|-------------|
| Móvil pequeño | 320px-480px | `@media (max-width: 480px)` |
| Móvil | 481px-768px | `@media (max-width: 768px)` |
| Tablet | 769px-1024px | `@media (max-width: 1024px)` |
| Desktop | 1025px+ | `@media (min-width: 1025px)` |

**Estrategias de diseño**:

```css
/* Mobile-First (recomendado) */
/* Estilos base para móvil */
.container {
    width: 100%;
    padding: 10px;
}

/* Tablets y superior */
@media (min-width: 768px) {
    .container {
        width: 750px;
        padding: 20px;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .container {
        width: 1200px;
    }
}

/* Desktop-First */
/* Estilos base para desktop */
.container {
    width: 1200px;
}

/* Tablets */
@media (max-width: 1024px) {
    .container {
        width: 750px;
    }
}

/* Móviles */
@media (max-width: 768px) {
    .container {
        width: 100%;
    }
}
```

**Media queries avanzadas**:

```css
/* Orientación */
@media (orientation: landscape) {
    /* Modo apaisado */
}

@media (orientation: portrait) {
    /* Modo vertical */
}

/* Rango de ancho */
@media (min-width: 768px) and (max-width: 1024px) {
    /* Solo tablets */
}

/* Resolución alta (Retina) */
@media (-webkit-min-device-pixel-ratio: 2),
       (min-resolution: 192dpi) {
    /* Pantallas Retina */
}

/* Preferencia de usuario */
@media (prefers-color-scheme: dark) {
    /* Modo oscuro */
}

@media (prefers-reduced-motion) {
    /* Sin animaciones para accesibilidad */
    * {
        animation: none !important;
        transition: none !important;
    }
}
```

#### 9. Unidades de medida CSS

```css
.container {
    max-width: 1200px;    /* Píxeles */
    padding: 2rem;        /* REM */
    margin: 0 auto;       /* Auto */
    height: 100vh;        /* Viewport Height */
}
```

**Tabla de unidades**:

| Unidad | Tipo | Descripción | Cuándo usar |
|--------|------|-------------|-------------|
| `px` | Absoluta | Píxeles fijos | Bordes, sombras, detalles precisos |
| `rem` | Relativa | Relativo a la raíz (16px) | Tamaños de fuente, espaciados |
| `em` | Relativa | Relativo al padre | Evitar (puede ser confuso) |
| `%` | Relativa | Porcentaje del padre | Anchos responsive |
| `vw` | Viewport | 1% del ancho de ventana | Anchos completos |
| `vh` | Viewport | 1% del alto de ventana | Alturas completas |
| `fr` | Grid | Fracción del espacio | CSS Grid |

**Ejemplos comparativos**:

```css
/* REM vs EM */
html { font-size: 16px; }

.padre { font-size: 20px; }

.hijo {
    font-size: 2rem;  /* 32px (2 × 16px raíz) */
    font-size: 2em;   /* 40px (2 × 20px padre) */
}

/* Viewport units */
.hero {
    height: 100vh;     /* Altura completa de la ventana */
    width: 100vw;      /* Ancho completo de la ventana */
}

.titulo {
    font-size: 5vw;    /* Se adapta al ancho de ventana */
}

/* Porcentajes */
.sidebar {
    width: 25%;        /* 25% del contenedor padre */
}

.contenido {
    width: 75%;        /* 75% del contenedor padre */
}
```

**Cuándo usar cada una**:

```css
/* Píxeles: Valores fijos pequeños */
border: 1px solid black;
box-shadow: 0 2px 4px rgba(0,0,0,0.1);

/* REM: Textos y espaciados */
font-size: 1.2rem;
padding: 2rem;
margin-bottom: 1.5rem;

/* Porcentajes: Layouts responsive */
width: 100%;
max-width: 80%;

/* Viewport: Secciones a pantalla completa */
min-height: 100vh;
width: 100vw;
```

#### 10. Position (Posicionamiento)

```css
header {
    position: sticky;
    top: 0;
    z-index: 1000;
}
```

**Tipos de position**:

| Valor | Comportamiento | Cuándo usar |
|-------|----------------|-------------|
| `static` | Por defecto, flujo normal | No especificar |
| `relative` | Relativo a su posición original | Ajustes pequeños, contexto para absolute |
| `absolute` | Relativo al ancestro positioned | Elementos flotantes, tooltips |
| `fixed` | Fijo en la ventana | Headers fijos, botones flotantes |
| `sticky` | Relativo hasta cierto punto, luego fijo | Menús que se quedan al hacer scroll |

**Ejemplos prácticos**:

```css
/* Sticky header */
header {
    position: sticky;
    top: 0;           /* Se pega al llegar arriba */
    z-index: 100;
}

/* Botón flotante */
.boton-whatsapp {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 999;
}

/* Badge en esquina */
.contenedor {
    position: relative;  /* Crea contexto */
}

.badge {
    position: absolute;
    top: -10px;
    right: -10px;
}

/* Overlay modal */
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0,0,0,0.5);
}

/* Centrado con absolute */
.popup {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

---

## 🔧 Guía de Mantenimiento

### Cómo cambiar colores del tema

#### Cambiar el gradiente principal

**Original**:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

**Ejemplos alternativos**:

```css
/* Azul cielo */
background: linear-gradient(135deg, #00d2ff 0%, #3a7bd5 100%);

/* Naranja-Rojo */
background: linear-gradient(135deg, #f12711 0%, #f5af19 100%);

/* Verde */
background: linear-gradient(135deg, #a8e063 0%, #56ab2f 100%);

/* Rosa-Morado */
background: linear-gradient(135deg, #ff6e7f 0%, #bfe9ff 100%);

/* Negro-Gris */
background: linear-gradient(135deg, #434343 0%, #000000 100%);
```

#### Cambiar colores de texto y elementos

**Buscar y reemplazar** estos valores:

| Elemento | Color original | Buscar | Reemplazar por |
|----------|----------------|--------|----------------|
| Títulos (h2) | Morado | `#667eea` | Tu color |
| Fondo oscuro | Azul oscuro | `#2c3e50` | Tu color |
| Bordes | Azul medio | `#34495e` | Tu color |
| Hover/Focus | Morado | `#667eea` | Tu color |

**Ejemplo de cambio completo a azul**:

```css
/* Buscar: #667eea */
/* Reemplazar: #00d2ff */

/* Buscar: #764ba2 */
/* Reemplazar: #3a7bd5 */
```

### Cómo modificar el diseño

#### Cambiar ancho máximo del contenido

```css
/* Original */
.container {
    max-width: 1200px;
}

/* Más estrecho (mejor para lectura) */
.container {
    max-width: 960px;
}

/* Más ancho (más contenido visible) */
.container {
    max-width: 1400px;
}
```

#### Ajustar número de columnas en servicios

```css
/* Original: automático responsive */
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));

/* Siempre 2 columnas */
grid-template-columns: repeat(2, 1fr);

/* Siempre 4 columnas */
grid-template-columns: repeat(4, 1fr);

/* Mínimo más ancho = menos columnas */
grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
```

#### Cambiar tamaños de fuente

```css
/* Títulos principales */
.hero h1 {
    font-size: 3rem;    /* Original: 48px */
    font-size: 4rem;    /* Más grande: 64px */
    font-size: 2.5rem;  /* Más pequeño: 40px */
}

/* Títulos de sección */
section h2 {
    font-size: 2.5rem;  /* Original: 40px */
}

/* Texto normal */
body {
    font-size: 1rem;    /* 16px por defecto */
    font-size: 1.125rem; /* 18px - más legible */
}
```

### Cómo agregar nueva sección

**Plantilla básica**:

```html
<section id="nueva-seccion">
    <div class="container">
        <h2>Título de la Nueva Sección</h2>
        <div class="contenido-seccion">
            <!-- Tu contenido aquí -->
        </div>
    </div>
</section>
```

**Añadir al menú**:

```html
<nav>
    <ul>
        <li><a href="#servicios">Servicios</a></li>
        <li><a href="#quienes-somos">Quiénes Somos</a></li>
        <li><a href="#nueva-seccion">Nueva Sección</a></li>
        <li><a href="#contacto">Contacto</a></li>
    </ul>
</nav>
```

**Estilos CSS**:

```css
#nueva-seccion {
    background: white; /* o #f8f9fa para alternar */
    padding: 4rem 0;
}
```

### Cómo agregar más servicios

**Copiar y modificar este bloque**:

```html
<div class="servicio-card">
    <h3>Nombre del Nuevo Servicio</h3>
    <p>Descripción detallada del servicio que ofreces.</p>
</div>
```

El grid se adaptará automáticamente al nuevo elemento.

### Cómo modificar el formulario

#### Agregar nuevo campo

```html
<div class="form-group">
    <label for="empresa">Empresa</label>
    <input type="text" id="empresa" name="empresa">
</div>
```

#### Cambiar campo a desplegable

```html
<div class="form-group">
    <label for="asunto">Asunto</label>
    <select id="asunto" name="asunto" required>
        <option value="">Selecciona un asunto</option>
        <option value="presupuesto">Solicitar presupuesto</option>
        <option value="soporte">Soporte técnico</option>
        <option value="informacion">Más información</option>
    </select>
</div>
```

#### Agregar checkbox

```html
<div class="form-group">
    <label>
        <input type="checkbox" name="aceptar" required>
        Acepto la <a href="#privacidad">política de privacidad</a>
    </label>
</div>
```

### Cómo hacer el formulario funcional

El formulario actual **no envía datos** porque no tiene backend. Opciones:

#### Opción 1: FormSpree (gratis, sin programación)

```html
<form action="https://formspree.io/f/TU_ID_AQUI" method="POST">
    <!-- Campos del formulario -->
</form>
```

1. Registrarse en [formspree.io](https://formspree.io)
2. Obtener tu ID único
3. Reemplazar `TU_ID_AQUI`

#### Opción 2: Netlify Forms (si alojas en Netlify)

```html
<form name="contacto" method="POST" data-netlify="true">
    <!-- Campos del formulario -->
</form>
```

#### Opción 3: EmailJS (envío desde JavaScript)

```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script>
    emailjs.init("TU_PUBLIC_KEY");
    
    document.querySelector('