<!-- l10n-sync: source-file="setup.md" -->
# Configuración del Taller

Para completar este taller necesitarás Visual Studio 2026, el SDK de .NET 10 y una cuenta de GitHub con acceso a GitHub Copilot.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- **Visual Studio 2026** con la extensión de GitHub Copilot instalada
- **SDK de .NET 10** instalado
- **Cuenta de GitHub** con una de las siguientes opciones:
  - [GitHub Copilot Free](https://github.com/features/copilot) - Nivel gratuito con uso limitado
  - [GitHub Copilot Pro](https://github.com/features/copilot) - Acceso completo (prueba gratuita de 30 días disponible)
  - GitHub Copilot a través de tu organización

> [!TIP]
> Si aún no tienes GitHub Copilot, puedes [registrarte en Copilot Free](https://github.com/features/copilot) o iniciar una [prueba gratuita de Copilot Pro](https://github.com/github-copilot/signup).

## Instalar la extensión .github + MCP

Antes de comenzar, instalemos la extensión .github + MCP para Visual Studio. Esta extensión proporciona acceso a los servidores MCP de GitHub que utilizaremos más adelante en el laboratorio.

1. [] Abre Visual Studio 2026
1. [] Ve a **Extensions -> Manage Extensions**
1. [] Busca **.github + MCP** en el cuadro de búsqueda
1. [] Haz clic en **Install** en la extensión **.github + MCP** de Mads Kristensen
1. [] Reinicia Visual Studio si se te solicita

> [!TIP]
> También puedes instalar esta extensión desde el [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.GitHubNode). La extensión .github + MCP es importante porque proporciona el runtime de Node.js requerido por algunos servidores MCP, que usarás en la Parte 9 de este laboratorio.

## Iniciar sesión en GitHub Copilot

1. [] Abre tu navegador y ve a `https://github.com`.
1. [] Inicia sesión con tu cuenta de GitHub o crea una nueva cuenta si no tienes una.
1. [] Abre Visual Studio 2026.
1. [] Selecciona **Continue without code**. Si se te solicita iniciar sesión, puedes hacer clic en Close.
1. [] Haz clic en el icono de Copilot en la barra superior (lado izquierdo junto al cuadro de búsqueda).
1. [] Haz clic en **Sign in to use Copilot**.
1. [] Se abrirá una ventana del navegador pidiéndote que inicies sesión en GitHub y autorices Visual Studio y Copilot. Completa el inicio de sesión y haz clic en **Authorize** cuando se te solicite.
1. [] Cuando el navegador muestre la confirmación, haz clic en **Open** para regresar a Visual Studio.
1. [] Después de la configuración, deberías ver la pestaña **GitHub Copilot Walkthrough** y el botón de Copilot debería estar verde.

> [!NOTE]
> Para los ejercicios prácticos del laboratorio que crean o modifican datos del repositorio a través de cloud agents (Parte 12), necesitarás hacer fork del repositorio del laboratorio en tu propia cuenta. Esto le da al cloud agent permisos para operar en tu fork.

## Activar la configuración de Copilot

1. [] Asegúrate de que Code Completions y Next Edit Suggestions estén habilitados:
   - Ve a la configuración de Code Completions en Visual Studio dirigiéndote a **Tools -> Options -> Text Editor -> Code Completions**
   - Asegúrate de que **Copilot Completions** esté marcado.
   - Asegúrate de que **Copilot Next Edit Suggestions** esté marcado.

   ![](./images/0-enable-nes.png)

1. [] Dirígete a **Tools -> Options -> GitHub -> Copilot -> Copilot Chat** y asegúrate de que las siguientes configuraciones estén habilitadas:
   - **Enable Planning**
   - **Enable View Plan Execution**
   - **Enable Copilot Coding agent (Preview)**


## Clonar el repositorio del laboratorio

Para la experiencia completa—especialmente si planeas delegar tareas a cloud agents o permitir que Copilot cree issues y suba cambios—haz fork del repositorio a tu propia cuenta de GitHub y clona tu fork.

1. [] En tu navegador, ve a `https://github.com/copilot-dev-days/visual-studio-lab` y haz clic en **Fork** para crear un fork en tu cuenta de GitHub.
1. [] En Visual Studio, haz clic en **File -> Clone Repository**.
1. [] Ingresa la URL de tu fork (por ejemplo `https://github.com/<your-username>/visual-studio-github-copilot-lab`) y presiona **Clone**.

Si prefieres no hacer fork, también puedes clonar el repositorio upstream directamente:

1. [] En Visual Studio, haz clic en **File -> Clone Repository**.
1. [] Ingresa `https://github.com/copilot-dev-days/visual-studio-lab` y presiona **Clone**.

El código ahora está abierto en Visual Studio. Siéntete libre de explorarlo o salta a la siguiente sección para iniciar la aplicación.

## Iniciar la aplicación

1. [] Abre el **Solution Explorer** desde el menú **View -> Solution Explorer**.
1. [] Establece **TinyShop.AppHost** como proyecto de inicio si aún no lo es, haciendo clic derecho en **TinyShop.AppHost** y seleccionando **Set as Startup Project**. Inicia el proyecto con F5 o **Debug -> Start Debugging** desde el menú.

    El .NET Aspire AppHost iniciará dos aplicaciones y el .NET Aspire Dashboard:

    - La aplicación backend .NET en **https://localhost:7130/api/Product**
    - La aplicación frontend Blazor en **https://localhost:7085** - Puedes ver la aplicación abriendo esa URL desde el dashboard

1. [] Detén la depuración y cierra la aplicación.

## Resumen y Próximos Pasos

Has configurado tu entorno y clonado el repositorio que usarás durante el resto del taller. ¡Comencemos a explorar GitHub Copilot!

---

[Siguiente: Parte 00 - Explorando el código fuente](./part00-exploring-codebase.md)
