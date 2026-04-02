<!-- l10n-sync: source-file="part09-mcp.md" -->
# Parte 09: MCP Servers

Model Context Protocol (MCP) es un protocolo abierto que estandariza cómo las aplicaciones proporcionan contexto a los modelos de lenguaje grandes (LLMs). Los MCP Servers amplían las capacidades de GitHub Copilot al conectarse a herramientas y servicios externos, dándole acceso a datos en tiempo real y la capacidad de realizar acciones.

En esta parte, aprenderás cómo agregar MCP Servers a Visual Studio y usarlos para obtener información sobre la optimización de tu aplicación.

## Agregando MCP Servers desde la galería

Visual Studio proporciona una galería de MCP Servers preconfigurados que puedes agregar fácilmente a tu proyecto.

Para ver tus herramientas existentes y MCP Servers instalados:
1. [] Abre la ventana de Copilot Chat haciendo clic en el icono de GitHub Copilot y seleccionando **Open Chat Window** o presiona `Ctrl+\+C`.
1. [] Haz clic en el icono de **Tools** en la parte inferior de la ventana de chat para abrir la configuración del MCP server.

   ![MCP Tools icon](./images/9-mcp-tools.png)
1. Aparecerán las herramientas integradas y las de MCP Servers.
1. Haz clic en el icono **+** para agregar un nuevo MCP server.
1. 
   ![Add MCP server](./images/9-add-mcp-server.png)
1. Especifica lo siguiente
1. **Destination**: Solution
1. **Server Id**: `github`
1. **Type**: HTTP
1. **URL**: https://api.githubcopilot.com/mcp/

   ![GitHub MCP server configuration](./images/9-github-mcp-server.png)


1. El MCP de GitHub requiere autenticación. Desde el **Solution Explorer**, expande **SolutionItems** y abre **.mcp.json**, y verás un mensaje de **Authentication required**. Haz clic en él y luego en Authenticate. Después de esto verás que está en línea y listo para usar.
   ![GitHub MCP authentication](./images/9-github-mcp-authentication.png)


Visual Studio 2026 tiene una galería MCP integrada para ayudarte a instalar fácilmente MCP Servers:

1. [] En Visual Studio 2026 ve a **Extensions -> MCP Registries...** para abrir la ventana de gestión de MCP Servers.
 
   ![MCP Registries menu](./images/9-mcp-registries-menu.png)

1. [] Explora los MCP Servers existentes en la galería.

> [!TIP]
> Los MCP Servers pueden proporcionar acceso a documentación, APIs y otros servicios que pueden ayudar a Copilot a darte respuestas más precisas y contextuales.



## Usando MCP Servers para obtener información

Ahora que tienes los MCP Servers de Microsoft Learn y GitHub instalados, usémoslos para obtener información sobre la optimización de la carga de activos en la aplicación.

1. [] En Copilot Chat, cambia a modo **Agent**. 
1. [] Asegúrate de que el MCP server de Microsoft Learn esté seleccionado como herramienta activa. Si no lo ves, haz clic en una nueva sesión de chat o cambia de modo:
  ![Select MCP server](./images/9-select-mcp-server.png)
1. [] Escribe el siguiente prompt: `Using the Microsoft Learn docs mcp, what are the best practices for optimizing image loading and asset delivery in a Blazor Server application?`
1. [] Revisa la respuesta de Copilot, que ahora tiene acceso a la documentación más reciente de Microsoft a través del MCP server.

## Creando issues de GitHub con MCP

El MCP server de GitHub permite que Copilot interactúe con tu repositorio de GitHub. Usémoslo para crear issues para mejoras que queremos hacer a la aplicación.

1. [] Asegúrate de que el MCP server de GitHub esté seleccionado como herramienta activa en Copilot Chat.
1. [] En la misma sesión de chat, escribe: `Based on the asset optimization recommendations, create 3 GitHub issues for improving the TinyShop application's performance.`

   > NOTA:
   > Copilot usará el MCP server de GitHub para crear los issues directamente en tu repositorio. Es posible que se te solicite autorizar la acción.

1. [] Revisa los issues que Copilot propone crear.
1. [] Aprueba la creación de los issues cuando se te solicite.
1. [] Navega a tu repositorio de GitHub para verificar que los issues se hayan creado.

**Punto clave**: Los MCP Servers amplían las capacidades de GitHub Copilot al conectarlo con servicios externos y documentación. Esto permite que Copilot proporcione información más precisa y actualizada, y realice acciones como crear issues de GitHub directamente desde la interfaz de chat.

---

[Atrás: Parte 08 - Descripciones de resumen de commit](./part08-commit-summary-descriptions.md) | [Siguiente: Parte 10 - Planning Mode en Agent](./part10-planning-mode.md)
