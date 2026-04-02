<!-- l10n-sync: source-file="part03-referencing-files.md" -->
# Parte 03: Referenciando archivos de código en el Chat

En esta sección, aprenderás cómo referenciar archivos de código existentes en tus conversaciones de chat.

1. [] Abre **Products.razor** nuevamente desde el proyecto **Store**.
1. [] Asegúrate de que GitHub Copilot Chat esté abierto haciendo clic en GitHub Copilot Chat en la esquina superior derecha de Visual Studio y seleccionando **Open Chat Window** o presiona `Ctrl+\+C` si el chat de Copilot no está abierto.

   ![Open chat window dialog](./images/1-open-copilot-chat.png)

1. Cambia el modo a `Ask`

	![Change to chat](./images/3-chat.png)

1. Inicia un nuevo chat haciendo clic en el icono `+` en la esquina superior derecha de la ventana de chat.

   ![New chat](./images/5-new-edits.png)

1. [] Escribe: `#ProductService.cs` para referenciar el archivo ProductService.
1. [] Pregunta: `How would I implement getting and visualizing the products in a table using the code in #ProductService and the css required.`
1. [] Revisa la sugerencia de código pero no la implementes aún.
1. [] Observa cómo Copilot puede referenciar código existente para proporcionar sugerencias contextuales.

**Punto clave**: Referenciar archivos en tu chat le proporciona a Copilot el contexto que necesita para dar sugerencias más precisas y específicas del proyecto.

---

[Atrás: Parte 02 - Mejorando la UI con Inline Chat](./part02-enhancing-ui.md) | [Siguiente: Parte 04 - Usando instrucciones personalizadas](./part04-custom-instructions.md)
