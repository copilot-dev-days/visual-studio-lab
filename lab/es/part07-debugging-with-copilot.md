<!-- l10n-sync: source-file="part07-debugging-with-copilot.md" -->
# Parte 07: Depurando con Copilot

En esta sección, aprenderás cómo usar Copilot para depurar una excepción en tu aplicación.

1. [] Depura el proyecto **AppHost** si aún no lo has hecho, y abre la **store** desde el .NET Aspire dashboard.
1. [] Haz clic en el botón **Go to About** en el menú de navegación.
1. [] Observa que ocurre una excepción y la aplicación se cuelga.
1. [] Presiona la opción **Analyze with Copilot** en la ventana emergente.

    ![Pop up for exception with Analyze with Copilot option](./images/7-ask-copilot-exception.png)

1. [] Revisa cómo Copilot trae información del depurador, incluyendo trazas de pila y estados de variables.
1. [] Observa cómo Copilot recomienda una corrección para el problema o proporciona sugerencias de código para resolverlo.

**Punto clave**: Copilot puede asistir en el diagnóstico y corrección de excepciones analizando la información del depurador y proporcionando recomendaciones accionables.

## Usando ventanas de inspección y visualizadores

En esta subsección, aprenderás cómo usar Copilot para analizar variables usando ventanas de inspección y visualizadores.

1. [] Abre el archivo **Products.razor** nuevamente desde el proyecto **Products**.
1. [] Agrega un punto de interrupción al final del método **OnInitializedAsync**.
1. [] Depura el **TinyShop.AppHost** y abre la **store** desde el .NET Aspire dashboard, y navega a la página de **Products**.
1. [] Cuando se alcance el punto de interrupción, pasa el cursor sobre la variable **imagePrefix**.
1. [] Presiona el botón **Copilot** para analizar la variable **imagePrefix**.

    ![Copilot button on variable](./images/7-inspect-variable.png)

    >Nota: también puedes ver estos en las ventanas de Locals o Watch

1. [] Observa cómo Copilot proporciona información detallada sobre la variable, incluyendo su valor y posibles problemas.
1. [] Pasa el cursor sobre la colección **products** y haz clic en el botón **View** con el icono de lupa.

    ![View button on products](./images/7-view-products.png)

1. [] Usa el visualizador para inspeccionar el contenido de la colección **products**.
1. [] Haz clic en el botón Generate expression y, en lenguaje natural, escribe: `Products that have the name outdoor in them and are under 40 dollars`
1. [] Observa cómo Copilot genera la expresión apropiada automáticamente.

    ![Generate expression for visualizer](./images/7-visualizer-sparkle.png)

**Punto clave**: Copilot puede mejorar la depuración proporcionando información detallada sobre variables a través de ventanas de inspección y visualizadores. Copilot puede simplificar tareas complejas de depuración generando expresiones y consultas LINQ basadas en entrada de lenguaje natural.

---

[Atrás: Parte 06 - Usando Copilot Vision](./part06-copilot-vision.md) | [Siguiente: Parte 08 - Descripciones de resumen de commit](./part08-commit-summary-descriptions.md)
