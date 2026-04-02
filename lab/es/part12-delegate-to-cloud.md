<!-- l10n-sync: source-file="part12-delegate-to-cloud.md" -->
# Parte 12: Delegar a la nube

A veces tienes una idea para una funcionalidad o mejora que quieres implementar, pero no tienes tiempo para trabajar en ella ahora mismo. Cloud Agent de GitHub Copilot te permite delegar tareas para que se ejecuten en la nube, liberándote para enfocarte en otro trabajo mientras Copilot implementa los cambios.

En esta parte, aprenderás cómo delegar una tarea a la nube para agregar un tema oscuro a la aplicación TinyShop.

## Entendiendo la delegación a la nube

Cloud Agent te permite:
- Enviar tareas complejas para que se ejecuten en la nube
- Continuar trabajando en otras tareas mientras el Cloud Agent implementa tu solicitud
- Revisar y aplicar los cambios cuando la tarea esté completa
- Recibir notificaciones cuando el trabajo esté terminado

Esto es particularmente útil para:
- Tareas grandes de refactorización
- Agregar nuevas funcionalidades que requieren cambios en múltiples archivos
- Implementaciones que consumen tiempo y no necesitan tu atención inmediata

## Preparando tu solicitud

Antes de delegar a la nube, es importante escribir un prompt claro y detallado. El Cloud Agent no tiene acceso a tu contexto inmediato, por lo que tu prompt debe incluir toda la información necesaria.

1. [] Piensa en la funcionalidad que quieres implementar. Para este laboratorio, agregaremos un tema oscuro a la aplicación TinyShop.

1. [] Considera qué detalles necesitará el Cloud Agent:
   - ¿Qué colores debería usar el tema oscuro?
   - ¿Debería incluir un interruptor para que los usuarios cambien de tema?
   - ¿Dónde deberían colocarse los estilos del tema?
   - ¿Debería persistirse la preferencia de tema?

## Delegando a la nube

1. [] Abre Copilot Chat y cambia a modo **Agent**.


1. [] Ingresa un prompt detallado para la funcionalidad del tema oscuro:

   ```
   Add a dark theme to the TinyShop Blazor application with the following requirements:

   1. Create a dark color scheme:
      - Background: #1a1a2e
      - Secondary background: #16213e
      - Text: #eaeaea
      - Accent: #0f3460
      - Highlight: #e94560

   2. Add a theme toggle:
      - Place a sun/moon icon button in the navigation bar
      - Clicking it should switch between light and dark themes
      - Use smooth CSS transitions for the theme switch

   3. Implementation details:
      - Use CSS custom properties (variables) for colors
      - Add theme styles in a new site-theme.css file
      - The toggle should persist the user's preference using localStorage

   4. Apply the theme to:
      - Page background
      - Navigation bar
      - Product cards
      - Text and links
      - Buttons and form elements
   ```

1. [] Revisa el prompt para asegurarte de que incluya todos los detalles necesarios.
1. [] Haz clic en el botón **Send to Copilot Coding Agent** (icono de nube) en la parte inferior de la ventana de chat.

   ![Delegate to Cloud button](./images/12-delegate-cloud.png)
1. El Cloud Agent reconocerá la solicitud y comenzará a procesarla.
1. [] Se te pedirá confirmar la delegación y crear un issue. Haz clic en **Confirm** para continuar.
1. [] Después de que el issue haya sido creado, podrás ver el pull request de los cambios en Visual Studio o en GitHub.
  ![View Pull Request](./images/12-view-pull-request.png)

1. Al ver en GitHub, puedes ver los cambios propuestos en el pull request, y ver la sesión en tiempo real.


## Mientras la tarea se ejecuta

Después de enviar, verás una confirmación de que tu tarea ha sido delegada. Puedes:

1. [] Continuar trabajando en otras tareas en Visual Studio.
1. [] Verificar el estado de tu tarea en la nube en la ventana de pull request.
1. [] Recibir una notificación cuando la tarea esté completa.

> [!TIP]
> Las tareas de Cloud Agent generalmente tardan varios minutos en completarse, dependiendo de la complejidad de la solicitud.


## Probando el tema oscuro

1. [] Una vez que el Cloud Agent haya completado la tarea, revisa los cambios en el pull request y haz checkout del branch en el que se realizaron los cambios.
1. [] Ejecuta la aplicación con F5 o Debug -> Start Debugging.
1. [] Haz clic en el botón de cambio de tema en la barra de navegación.
1. [] Verifica que el tema oscuro se aplique correctamente.
1. [] Actualiza la página y verifica que la preferencia de tema se mantenga.
1. [] Cambia de vuelta al tema claro y verifica que funcione en ambas direcciones.

**Punto clave**: Delegar a la nube te permite trasladar tareas complejas a GitHub Copilot mientras te enfocas en otro trabajo. Esto es especialmente valioso para implementaciones que consumen tiempo o cuando quieres explorar ideas sin bloquear tu flujo de trabajo inmediato.

---

🎉 **¡Felicidades!** ¡Has completado las 13 partes del taller!

[Atrás: Parte 11 - Prompt Files reutilizables](./part11-reusable-prompts.md) | [🎊 ¡Taller completado!](complete.html)
