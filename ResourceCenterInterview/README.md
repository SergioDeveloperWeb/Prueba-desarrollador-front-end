# Entorno de Entrevista: Resource Center

Entorno reducido y ejecutable para la prueba técnica frontend sobre el stack **ASP.NET Core MVC + Razor + jQuery + SCSS**.

---

## Requisitos Previos

El entorno ha sido completamente estabilizado y cuenta con todos los ejecutables portables instalados localmente. Los requisitos del sistema son:
*   **Linux / Bash**
*   **Node.js** (opcional, el compilador SCSS está inyectado nativamente).
*   **SDK de .NET 8.0** (instalado localmente en `~/.dotnet`).

---

## Guía de Arranque Paso a Paso (Foolproof)

Sigue estos pasos en secuencia para inicializar y ejecutar el proyecto de forma local:

### Paso 1: Restaurar Paquetes de .NET
Para restaurar las dependencias del servidor ASP.NET Core utilizando el SDK local de .NET 8.0, ejecuta desde la carpeta `ResourceCenterInterview`:

```bash
# Restauración utilizando el ejecutable local
~/.dotnet/dotnet restore --configfile NuGet.config
```

### Paso 2: Descargar Compilador SCSS e Instalar Dependencias Frontend
El compilador de Sass no está incluido en el repositorio. Descarga el compilador nativo y portable de **Dart Sass** ejecutando desde la carpeta `ResourceCenterInterview`:

```bash
# Descargar y extraer Dart Sass (Linux x64)
curl -sL https://github.com/sass/dart-sass/releases/download/1.77.2/dart-sass-1.77.2-linux-x64.tar.gz -o dart-sass.tar.gz && tar -xzf dart-sass.tar.gz && rm dart-sass.tar.gz
```

> 💡 **Alternativa (si tienes npm instalado):** Puedes usar `npm install` y luego `npm run scss:build` en lugar de los pasos anteriores.

### Paso 3: Compilar SCSS a CSS (Hojas de Estilo)
Para compilar el archivo SCSS principal en su hoja de estilos CSS correspondiente, ejecuta:

```bash
# Compilar SCSS a CSS una única vez
./dart-sass/sass --no-source-map wwwroot/technical-test/resource-center.scss wwwroot/technical-test/resource-center.css
```

> 💡 **Nota (Modo Observador):** Si deseas realizar modificaciones estéticas y que se compilen automáticamente en caliente al guardar, puedes ejecutar:
> ```bash
> ./dart-sass/sass --watch wwwroot/technical-test/resource-center.scss:wwwroot/technical-test/resource-center.css
> ```

### Paso 4: Levantar el Servidor de Aplicación
Para ejecutar el servidor web local bajo el perfil HTTP de desarrollo, ejecuta:

```bash
# Iniciar el servidor web
~/.dotnet/dotnet run --launch-profile http
```

### Paso 5: Visualizar en el Navegador
Una vez que la consola muestre el mensaje `Now listening on: http://localhost:5087`, abre tu navegador e ingresa a la siguiente URL para probar la aplicación interactiva:

👉 **[http://localhost:5087/TechnicalTest/ResourceCenter](http://localhost:5087/TechnicalTest/ResourceCenter)**

---

## Estructura del Reto Técnico

Los archivos que componen la prueba técnica y que han sido completamente resueltos y estilizados son:

*   **Lógica Interactiva (JS / jQuery):** `wwwroot/technical-test/resource-center.js`
*   **Hoja de Estilos (Sass):** `wwwroot/technical-test/resource-center.scss`
*   **Estructura Razor (HTML / XML):** `Views/TechnicalTest/ResourceCenter.cshtml`
*   **Datos Simulados (JSON):** `Data/resources.mock.json`
