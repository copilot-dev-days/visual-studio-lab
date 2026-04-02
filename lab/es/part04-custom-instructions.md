<!-- l10n-sync: source-file="part04-custom-instructions.md" -->
# Parte 04: Usando instrucciones personalizadas

Siempre hay piezas clave de información que cualquier persona que genere código para tu base de código necesita saber: las tecnologías en uso, los estándares de codificación a seguir, la estructura del proyecto, etc. Dado que el contexto es tan importante, como hemos discutido, probablemente queremos asegurarnos de que Copilot siempre tenga esta información también. Afortunadamente, podemos proporcionar esta visión general mediante el uso de instrucciones de Copilot.

Antes de comenzar actualizaciones más grandes al sitio con la ayuda de Copilot, queremos asegurarnos de que Copilot tenga una buena comprensión de cómo estamos construyendo nuestra aplicación. Por eso, vamos a agregar un archivo de instrucciones de Copilot al repositorio.

Las instrucciones de Copilot son un archivo markdown ubicado en tu carpeta **.github**. Se convierte en parte de tu proyecto y, a su vez, está disponible para todos los colaboradores de tu código fuente. Puedes usar este archivo para indicar varios estándares de codificación que deseas seguir, las tecnologías que usa tu proyecto o cualquier otra cosa importante para que GitHub Copilot Chat entienda al generar sugerencias.

> [!IMPORTANT]
> El archivo *copilot-instructions.md* se incluye en **cada** llamada a GitHub Copilot Chat y será parte del contexto enviado a Copilot. Debido a que siempre hay un conjunto limitado de tokens con los que un LLM puede operar, un archivo de instrucciones de Copilot grande puede ocultar información relevante. Por lo tanto, debes limitar tu archivo de instrucciones de Copilot a información a nivel de proyecto, proporcionando una visión general de lo que estás construyendo y cómo lo estás construyendo. Si necesitas proporcionar información más específica para tareas particulares, puedes crear [Prompt Files](https://docs.github.com/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot?tool=vscode#about-prompt-files).

Aquí hay algunas pautas a considerar al crear un archivo de instrucciones de Copilot:

- El archivo de instrucciones de Copilot se convierte en parte del proyecto, lo que significa que se aplicará a todos los desarrolladores; cualquier cosa indicada en el archivo debe ser aplicable globalmente.
- El archivo es markdown, por lo que puedes aprovechar ese hecho agrupando contenido para mejorar la legibilidad.
- Proporciona una visión general de **qué** estás construyendo y **cómo** lo estás construyendo, incluyendo:
    - lenguajes, frameworks y bibliotecas en uso.
    - activos requeridos a generar (como pruebas unitarias) y dónde deben colocarse.
    - cualquier regla específica del lenguaje.
- Si notas que GitHub Copilot proporciona consistentemente una sugerencia inesperada (por ejemplo, usar componentes de clase para React), agrega esas notas al archivo de instrucciones.

## Crear un archivo de instrucciones de Copilot

1. [] En el **Solution Explorer**, expande el **GitHub Node** y abre **copilot-instructions.md**

1. [] Agrega información específica del proyecto sobre tu aplicación:

    ```markdown
    ### Backend
    - Products project is the backend API.
    - Built with .NET Minimal APIs.
    - Uses Entity Framework Core with an in-memory database.
    - Should follow OpenAPI best practices.

    ### Frontend
    - Store project is a .NET 10 Blazor Server application.
    - Uses default Bootstrap styling.
    - UI should have a modern look and feel.
    - CSS should be in .razor.css files.
    ```
1. Inicia un nuevo chat haciendo clic en el icono `+` en la esquina superior derecha de la ventana de chat.

   ![New chat](./images/5-new-edits.png)

1. [] Regresa a Copilot Chat y vuelve a ejecutar el prompt de la Parte 03, puedes hacerlo presionando la tecla de flecha arriba. o
1. [] Pregunta: `How would I implement getting and visualizing the products in a table using the code in #ProductService and the css required.`
1. [] Revisa la sugerencia de código pero no la implementes aún.
1. [] Observa cómo las respuestas ahora incorporan tus instrucciones personalizadas.

**Punto clave**: Las instrucciones personalizadas hacen que las sugerencias de Copilot estén más alineadas con los estándares y preferencias de arquitectura de tu proyecto.

---

[Atrás: Parte 03 - Referenciando archivos de código en el Chat](./part03-referencing-files.md) | [Siguiente: Parte 05 - Implementando funcionalidades con Copilot Agent](./part05-implementing-features.md)
