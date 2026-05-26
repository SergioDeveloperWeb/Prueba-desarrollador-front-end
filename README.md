# Reto Técnico: Resource Center (Premium Minimalist Edition)

Esta es la solución optimizada y completamente resuelta para la prueba técnica frontend sobre el stack **ASP.NET Core MVC + Razor + jQuery + SCSS**.

El proyecto ha sido rediseñado visualmente bajo una estética minimalista premium y corregido a nivel funcional, garantizando accesibilidad (A11y), rendimiento y persistencia.

---

## 🛠️ Correcciones y Mejoras del Reto

Para este reto técnico se identificaron y solucionaron múltiples fallos de lógica y se añadieron mejoras clave:

### 1. Corrección de Bugs Funcionales (JavaScript / jQuery)
*   **Filtro de Categoría Invertido:** Se corrigió la condición lógica que excluía la categoría seleccionada en lugar de mostrarla.
*   **Búsqueda por Texto:** Se implementó la búsqueda en tiempo real que filtra recursos según coincidencias en el **título** y la **descripción** (ignorando mayúsculas/minúsculas y acentos).
*   **Contador de Recursos:** Se solucionó el bug del contador estático; ahora refleja dinámicamente la cantidad real de recursos filtrados en tiempo real (ej. *Mostrando 4 de 12 recursos*).
*   **Botón de Limpieza (Clear):** Se programó el botón para restablecer instantáneamente la caja de texto, deseleccionar categorías y recargar todos los recursos de forma fluida.
*   **Cierre de Modales (UX):** Se habilitó el cierre de los detalles del recurso presionando la tecla `Escape` y haciendo clic fuera del modal (en el fondo translúcido).
*   **Error de Tipo en `escapeHtml`:** Se corrigió un `TypeError` fatal en la consola provocado al pasar el `id` numérico a la función de saneamiento HTML.

### 2. Mejoras de UX & Accesibilidad (A11y)
*   **Persistencia de Estado:** Se integró `sessionStorage` para retener la consulta de búsqueda y la categoría seleccionada al recargar o refrescar el navegador.
*   **Diseño Accesible:** Se añadieron etiquetas `aria-label`, roles semánticos y soporte completo de navegación por teclado con estilos `:focus-visible` claramente delineados.

### 3. Rediseño Estético (Breathtaking SCSS Layout)
*   **Tipografía Moderna:** Se importó e integró la fuente **'Outfit'** de Google Fonts para dar un aire geométrico y elegante.
*   **Glassmorphism en Filtros:** El panel de filtros se convirtió en una tarjeta flotante translúcida con desenfoque de fondo (`backdrop-filter: blur(16px)`).
*   **Luxury 3D Cards:** Las tarjetas de recursos se elevan sutilmente en hover (`translateY(-6px)`) con sombras difusas coloreadas y un indicador superior con degradado dinámico según su categoría.
*   **Colores Curados:** Paleta moderna en tonos Slate/Indigo con etiquetas de colores pasteles legibles para cada tipo de recurso (Guías, Plantillas, Videos).

---

## 📋 Requisitos Previos

Antes de ejecutar el proyecto, asegúrate de tener instalado en tu sistema:
*   **SDK de .NET 8.0**
*   **Node.js & npm** *(Recomendado para compilar SCSS fácilmente de forma multiplataforma)*

---

## 🚀 Guía de Arranque (Paso a Paso)

Primero, abre tu terminal y posiciónate en el directorio de la aplicación:
```bash
cd ResourceCenterInterview
```

Ahora, elige la opción que mejor se adapte a tu sistema operativo o entorno:

### Opción A: Método Estándar (Recomendado - Windows, macOS y Linux)
Utiliza este método si dispones de **Node.js** y **.NET SDK** instalados de forma global en tu equipo.

1. **Restaurar paquetes de NuGet (.NET):**
   ```bash
   dotnet restore
   ```

2. **Instalar dependencias frontend y compilar SCSS:**
   ```bash
   # Instalar dependencias locales (incluyendo el compilador de Sass)
   npm install

   # Compilar SCSS a CSS una única vez
   npm run scss:build

   # (Opcional) Observar cambios en caliente durante el desarrollo
   npm run scss:watch
   ```

3. **Ejecutar el servidor:**
   Inicia el servidor local de desarrollo ASP.NET Core:
   ```bash
   dotnet run --launch-profile http
   ```

---

### Opción B: Método Portable (Solo Linux / Entornos Restringidos)
Utiliza este método si estás en un entorno Linux donde no posees permisos globales para instalar herramientas y deseas usar los ejecutables locales y portables del proyecto.

1. **Restaurar dependencias:**
   ```bash
   ~/.dotnet/dotnet restore --configfile NuGet.config
   ```

2. **Descargar compilador portable de Sass:**
   ```bash
   curl -sL https://github.com/sass/dart-sass/releases/download/1.77.2/dart-sass-1.77.2-linux-x64.tar.gz -o dart-sass.tar.gz && tar -xzf dart-sass.tar.gz && rm dart-sass.tar.gz
   ```

3. **Compilar estilos SCSS:**
   ```bash
   # Compilar una única vez
   ./dart-sass/sass --no-source-map wwwroot/technical-test/resource-center.scss wwwroot/technical-test/resource-center.css

   # (Opcional) Compilar en caliente
   ./dart-sass/sass --watch wwwroot/technical-test/resource-center.scss:wwwroot/technical-test/resource-center.css
   ```

4. **Ejecutar el servidor:**
   ```bash
   ~/.dotnet/dotnet run --launch-profile http
   ```

---

## 🌐 Visualización en el Navegador

Una vez que el servidor esté en funcionamiento por cualquiera de los métodos anteriores, abre tu navegador e ingresa a la siguiente dirección:

👉 **[http://localhost:5087/TechnicalTest/ResourceCenter](http://localhost:5087/TechnicalTest/ResourceCenter)**

---

## 📂 Estructura Clave del Proyecto
Los archivos modificados para cumplir con las especificaciones del reto son:
*   **Lógica Interactiva (JS / jQuery):** [ResourceCenterInterview/wwwroot/technical-test/resource-center.js](ResourceCenterInterview/wwwroot/technical-test/resource-center.js) — *Filtros, modales, persistencia y eventos.*
*   **Diseño y Hoja de Estilo (SCSS):** [ResourceCenterInterview/wwwroot/technical-test/resource-center.scss](ResourceCenterInterview/wwwroot/technical-test/resource-center.scss) — *Arquitectura CSS, variables, micro-animaciones y glassmorphism.*
*   **Estructura Razor (HTML):** [ResourceCenterInterview/Views/TechnicalTest/ResourceCenter.cshtml](ResourceCenterInterview/Views/TechnicalTest/ResourceCenter.cshtml) — *Estructura accesible y carga de assets.*

---

## 📝 Contexto Original del Reto
El objetivo original era completar una pantalla interna de `Resource Center` para que quedara usable, responsive y alineada con el stack actual.
Las tareas obligatorias requeridas eran:
1. Completar filtros por texto y por categoría, junto al botón limpiar.
2. Renderizar tarjetas correctamente resolviendo edge cases de datos.
3. Implementar el detalle del recurso abriendo un modal y cerrándolo con el botón y con la tecla `Escape`.
4. Ajustar estilos SCSS base y vista responsive (mobile y desktop).
5. Bonus de accesibilidad básica y persistencia en `sessionStorage` (ambos cubiertos).