# Entorno de Entrevista: Resource Center

Entorno reducido y ejecutable para la prueba técnica frontend sobre el stack **ASP.NET Core MVC + Razor + jQuery + SCSS**.

---

## Requisitos Previos

El entorno ha sido completamente estabilizado y cuenta con todos los ejecutables portables instalados localmente. Los requisitos del sistema son:
*   **Linux / Bash**
*   **Node.js** (opcional, el compilador SCSS está inyectado nativamente).
*   **SDK de .NET 8.0** (instalado localmente en `~/.dotnet`).

---

## Guía de Arranque Paso a Paso

Elige el método que mejor se adapte a tu entorno de desarrollo:

### Opción A: Método Estándar (Recomendado - Windows, macOS y Linux)
Utiliza este método si tienes instalados de forma global el **SDK de .NET** y **Node.js/npm**.

1. **Restaurar dependencias del servidor:**
   Desde la carpeta `ResourceCenterInterview`, ejecuta:
   ```bash
   dotnet restore
   ```

2. **Instalar compilador Sass y compilar estilos:**
   Instala las dependencias de desarrollo y compila el archivo SCSS a CSS:
   ```bash
   # Instalar dependencias
   npm install

   # Compilar una única vez
   npm run scss:build

   # (Opcional) Compilar en caliente durante el desarrollo
   npm run scss:watch
   ```

3. **Ejecutar el servidor:**
   Inicia la aplicación bajo el perfil HTTP de desarrollo:
   ```bash
   dotnet run --launch-profile http
   ```

---

### Opción B: Método Portable (Solo Linux / Sin dependencias globales)
Utiliza este método si estás en un entorno Linux sin `npm` ni el SDK de `.NET` instalado de forma global (usando las herramientas portables locales del proyecto).

1. **Restaurar dependencias del servidor:**
   Utiliza el SDK de .NET instalado localmente:
   ```bash
   ~/.dotnet/dotnet restore --configfile NuGet.config
   ```

2. **Descargar e instalar compilador Sass:**
   Descarga y extrae el compilador nativo y portable de **Dart Sass** (`v1.77.2`):
   ```bash
   curl -sL https://github.com/sass/dart-sass/releases/download/1.77.2/dart-sass-1.77.2-linux-x64.tar.gz -o dart-sass.tar.gz && tar -xzf dart-sass.tar.gz && rm dart-sass.tar.gz
   ```

3. **Compilar SCSS a CSS:**
   Compila el archivo de estilos:
   ```bash
   # Compilar una única vez
   ./dart-sass/sass --no-source-map wwwroot/technical-test/resource-center.scss wwwroot/technical-test/resource-center.css

   # (Opcional) Compilar en caliente durante el desarrollo
   ./dart-sass/sass --watch wwwroot/technical-test/resource-center.scss:wwwroot/technical-test/resource-center.css
   ```

4. **Ejecutar el servidor:**
   ```bash
   ~/.dotnet/dotnet run --launch-profile http
   ```

---

### Visualización en el Navegador
Una vez que el servidor esté activo (por cualquiera de los dos métodos), abre tu navegador en:

👉 **[http://localhost:5087/TechnicalTest/ResourceCenter](http://localhost:5087/TechnicalTest/ResourceCenter)**

---

## Estructura del Reto Técnico

Los archivos que componen la prueba técnica y que han sido completamente resueltos y estilizados son:

*   **Lógica Interactiva (JS / jQuery):** `wwwroot/technical-test/resource-center.js`
*   **Hoja de Estilos (Sass):** `wwwroot/technical-test/resource-center.scss`
*   **Estructura Razor (HTML / XML):** `Views/TechnicalTest/ResourceCenter.cshtml`
*   **Datos Simulados (JSON):** `Data/resources.mock.json`
