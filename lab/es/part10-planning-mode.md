<!-- l10n-sync: source-file="part10-planning-mode.md" -->
# Parte 10: Planning Mode en Agent

Cuando trabajas en funcionalidades complejas, es útil planificar antes de sumergirte en la implementación. Planning Mode de GitHub Copilot en Agent te permite crear un plan estructurado para implementar nuevas funcionalidades. Esto ayuda a asegurar que entiendas el alcance completo de los cambios necesarios antes de que se genere cualquier código.

En esta parte, usarás Planning Mode para planificar e implementar una funcionalidad que permite a los usuarios navegar directamente a la página de detalle de un producto específico.

## Entendiendo Planning Mode

Planning Mode es una funcionalidad en Agent que te ayuda a:
- Descomponer funcionalidades complejas en pasos manejables
- Entender todos los archivos y cambios necesarios antes de la implementación
- Revisar y refinar el plan antes de que Copilot comience a generar código

## Creando un plan para la navegación de productos

Usemos Planning Mode para implementar una funcionalidad que permita a los usuarios hacer clic en un producto en la página de listado y navegar a una página dedicada de detalle del producto.

1. [] Abre la ventana de Copilot Chat si no está abierta.
1. [] Crea una nueva sesión de chat.
1. [] Cambia a modo **Agent**.
1. [] Asegúrate de que **Planning** esté habilitado en las herramientas.

   ![Planning Mode enabled](./images/10-planning-mode.png)

1. [] Ingresa el siguiente prompt:

   ```
   Create a plan for the following: I want to add product navigation to the TinyShop application. When a user clicks on a product in the product listing page, they should be taken to a new product detail page that shows:
   - The product image (larger size)
   - Product name as the page title
   - Full description
   - Price
   - A "Back to Products" button

   The URL should be /product/{id} where id is the product ID.
   ```

1. [] Revisa el plan que Copilot genera. Debería incluir:
   - Crear un nuevo componente `ProductDetail.razor`
   - Actualizar la configuración de enrutamiento
   - Modificar el listado de productos para incluir enlaces de navegación
   - Agregar el estilo CSS necesario
   - Etc.

   ![Generated Plan](./images/10-generated-plan.png)

1. [] Si el plan se ve bien, haz clic en **Execute Plan** para comenzar la implementación.
1. [] Si deseas modificar el plan, puedes agregar instrucciones adicionales o pedir a Copilot que revise pasos específicos.

## Revisando y refinando el plan

Antes de ejecutar, es una buena práctica revisar el plan cuidadosamente:

1. [] Verifica que todos los archivos necesarios estén incluidos en el plan.
1. [] Verifica que el enfoque esté alineado con la estructura de tu proyecto y los estándares de codificación.
1. [] Agrega cualquier requisito faltante escribiendo instrucciones adicionales.

Por ejemplo, podrías agregar:

```
Update the plan to also ensure the product detail page handles cases where the product ID doesn't exist by showing a "Product not found" message.
```

## Ejecutando el plan

1. [] Una vez que estés satisfecho con el plan, indica a Copilot que **Execute Plan**.
1. [] Copilot implementará cada paso del plan, creando y modificando archivos según sea necesario.
1. [] Revisa los cambios en el editor a medida que se realizan.
1. [] Ejecuta la aplicación para probar la nueva funcionalidad de navegación de productos.

## Probando la funcionalidad

1. [] Inicia la aplicación con F5 o Debug -> Start Debugging.
1. [] Navega a la página de Products.
1. [] Haz clic en un producto del listado.
1. [] Verifica que seas llevado a la página de detalle del producto con la información correcta.
1. [] Haz clic en el botón "Back to Products" para regresar al listado.

**Punto clave**: Planning Mode te ayuda a pensar en funcionalidades complejas antes de la implementación. Al crear un plan estructurado, puedes asegurar que todos los cambios necesarios sean considerados y revisar el enfoque antes de que se genere cualquier código. Esto lleva a un código mejor organizado y menos iteraciones.

---

[Atrás: Parte 09 - MCP Servers](./part09-mcp.md) | [Siguiente: Parte 11 - Prompt Files reutilizables](./part11-reusable-prompts.md)
