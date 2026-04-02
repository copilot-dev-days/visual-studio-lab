<!-- l10n-sync: source-file="part06-copilot-vision.md" -->
# Parte 06: Usando Copilot Vision

En esta sección, usarás Copilot Vision. Puedes compartir capturas de pantalla de errores y Copilot interpretará la imagen y resolverá el problema. O comparte maquetas de nuevos diseños, y Vision te ayudará a darles vida. Actualicemos nuestro diseño basándonos en una foto que nos dio nuestro diseñador.

1. [] Abre un nuevo hilo de Copilot Chat en Agent mode.
1. [] Haz clic en el botón **+** en el chat, selecciona **upload image**, y selecciona la imagen **eshop.png** que se encuentra en la raíz del repositorio clonado.

    ![Attach image icon](./images/6-add-image.png)

1. [] Pregunta: `Update the Products.razor to display products in a grid layout similar to this image. Add nice hover effects and make it responsive.`
1. [] Revisa los cambios de código sugeridos e impleméntalos. Debería recomendar cambios tanto en **Products.razor** como en un nuevo **Products.razor.css**
1. [] Ejecuta la aplicación para ver el diseño actualizado de la cuadrícula de productos. Es posible que debas limpiar la caché del navegador con CTRL+SHIFT+R si no ves la actualización del CSS.

> [!NOTE]
> Continúa iterando con Copilot Agent si el resultado no es de tu agrado.

**Punto clave**: Copilot Vision puede comprender diseños de UI a partir de imágenes y ayudarte a implementarlos en tu aplicación.

---

[Atrás: Parte 05 - Implementando funcionalidades con Copilot Agent](./part05-implementing-features.md) | [Siguiente: Parte 07 - Depurando con Copilot](./part07-debugging-with-copilot.md)
