<!-- l10n-sync: source-file="part02-enhancing-ui.md" -->
# Parte 02: Mejorando la UI con Inline Chat

Ahora mejorarás la experiencia de carga usando Inline Chat de Copilot.

> NOTA: Este ejercicio proporciona prompts específicos para escribir, pero como parte de la experiencia de aprendizaje te animamos a descubrir cómo interactuar con Copilot. Siéntete libre de hablar en lenguaje natural, describiendo lo que estás buscando o necesitas lograr.

1. [] En el **Solution Explorer**, dentro del proyecto **Store**, abre **Components/Pages/Products.razor**.
1. [] Encuentra el texto "Loading..." en el código.
1. [] Selecciona este texto y haz clic derecho.
1. [] Elige "Chat" o presiona `Alt+/`.
1. [] En el Inline Chat, escribe: `Update this razor to have a simple spinner style, using built in bootstrap styles.`

    ![Screenshot of VS with inline chat](./images/2-inline-code.png)

1. [] Selecciona **Tab** para aceptar los cambios, y debería verse similar a:

    ```html
    <div class="spinner-border text-primary" role="status">
        <span class="visually-hidden">Loading...</span>
    </div>
    ```

1. [] Ejecuta la aplicación para ver tu nuevo spinner de carga en acción.

1. [] Detén la depuración y cierra la aplicación

**Punto clave**: Inline Chat te permite hacer mejoras específicas a tu código sin salir del contexto de tu editor.

---

[Atrás: Parte 01 - Code Completion con Ghost Text](./part01-code-completion.md) | [Siguiente: Parte 03 - Referenciando archivos de código en el Chat](./part03-referencing-files.md)
