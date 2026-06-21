# Mi Portafolio - App Web Envolvente (Iframe Container)

Este proyecto consiste en una página web estática diseñada para servir como un contenedor de pantalla completa adaptativo. Utiliza un elemento `iframe` para incrustar y visualizar de forma directa una aplicación web externa desarrollada en [Google Apps Script (GAS)](https://developers.google.com/apps-script).

## 🚀 Características

* **Pantalla Completa Automatizada**: Diseño optimizado sin márgenes que ocupa el 100% de la anchura y altura del navegador.
* **Completamente Adaptativo**: La interfaz del contenedor se ajusta dinámicamente a cualquier resolución de pantalla o dispositivo móvil.
* **Sin Barras de Desplazamiento Forzadas**: Propiedades de desbordamiento configuradas para evitar scroll innecesario en el contenedor principal.

## 🛠️ Estructura del Código

El archivo principal `index.html` contiene tres bloques estructurales mínimos:
1. **Meta tags**: Aseguran el renderizado correcto y la escala inicial en entornos móviles (`viewport`).
2. **Estilos CSS Embebidos**: Controlan que tanto el `html`, el `body`, como la clase `.iframe-container` eliminen márgenes nativos y hereden el tamaño completo disponible.
3. **Iframe**: Carga de forma asíncrona la URL de ejecución del script de Google.

## ⚙️ Configuración y Uso

Para desplegar tu propio portafolio o aplicación con este contenedor, sigue estos pasos:

1. **Clona o copia** el código del archivo `index.html` en tu servidor o entorno local.
2. **Obtén tu URL de ejecución** desde el editor de Google Apps Script (debe terminar en `/exec`).
3. **Modifica la etiqueta `iframe`** reemplazando el valor actual del atributo `src` con tu enlace personalizado:
   ```html
   <iframe src="TU_NUEVA_URL_DE_EXEC_AQUÍ"></iframe>
   ```
4. Abre el archivo en cualquier navegador web o súbelo a un servicio de hosting estático como [GitHub Pages](https://pages.github.com/).

## ⚠️ Notas Importantes de Compatibilidad

* **Permisos de X-Frame-Options**: Para que la aplicación web de Google Apps Script funcione correctamente dentro de este `iframe`, debes asegurarte de que tu archivo `Code.gs` configure el modo de sandbox adecuado utilizando el método `setXFrameOptionsMode`:
  ```javascript
  function doGet() {
    return HtmlService.createHtmlOutputFromFile('Index')
             .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
  }
  ```
  *Si omitas esta configuración, el navegador bloqueará la carga por motivos de seguridad perimetral ([Clickjacking protection](https://mozilla.org)).*

