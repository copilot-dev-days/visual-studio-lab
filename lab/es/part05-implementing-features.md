<!-- l10n-sync: source-file="part05-implementing-features.md" -->
# Parte 05: Implementando funcionalidades con Copilot Agent

Anteriormente utilizamos Copilot Chat, que es excelente para trabajar con un archivo individual o hacer preguntas sobre nuestro código. Sin embargo, muchas actualizaciones requieren cambios en múltiples archivos a lo largo de un código fuente. Incluso un cambio aparentemente básico en una página web probablemente requiere actualizar archivos HTML, CSS, Razor y C#. Copilot Agent te permite modificar múltiples archivos a la vez en tu proyecto, se auto-corrige y puede ejecutar comandos si se le otorga permiso, como instalar paquetes NuGet.

Con Copilot Agent, agregarás los archivos que necesitan ser actualizados al contexto. Una vez que proporcionas el prompt, Copilot Agent comenzará las actualizaciones en todos los archivos del contexto. También tiene la capacidad de crear nuevos archivos o agregar archivos al contexto según lo considere apropiado.

Agreguemos la capacidad de ver una lista de imágenes en la aplicación:

1. [] Abre GitHub Copilot Chat en la esquina superior derecha de Visual Studio y selecciona **Open Chat Window** o presiona `Ctrl+\+C` si el chat de Copilot no está abierto.

1. [] Cambia a modo **Agent**.

   ![Switch to agent mode](./images/1-agent.png)

1. [] En Visual Studio, abre un nuevo Copilot Chat con el icono **+** de chat.

    ![New chat icon in VS copilot](./images/5-new-edits.png)

1. [] En la parte inferior del panel de GitHub Copilot Chat, selecciona el modelo (el predeterminado es "GPT-4o") de la lista desplegable, y selecciona **Claude Opus 4.5** de la lista de modelos disponibles.

    ![Select Opus in Copilot](./images/5-select-sonnet.png)

1. [] Escribe: `Implement a simple product listing page in Products.razor that fetches products from #ProductService and displays them in a simple list with product name, description, price, and image.`

    > NOTA: Deberías usar tu propia redacción al generar el prompt. Como se destacó anteriormente, parte del ejercicio es sentirte cómodo creando prompts para GitHub Copilot. Un consejo clave es que siempre es bueno proporcionar más orientación para asegurarte de obtener el código que estás buscando.

    > NOTA: Si se te pide **Enable Claude Opus 4.5 for all clients** haz clic en el botón **Enable**.

Copilot Agent mode comienza a implementar las sugerencias de código.

## Revisando los cambios

A diferencia de nuestros ejemplos anteriores donde trabajamos con un archivo individual, ahora estamos trabajando con cambios en múltiples archivos - y tal vez múltiples secciones de múltiples archivos. Afortunadamente, Copilot Agent tiene funcionalidad para ayudar a agilizar este proceso.

GitHub Copilot propondrá los siguientes cambios a la aplicación, incluyendo la actualización de Products.razor, la adición de un Products.razor.css y posiblemente más.

1. [] Revisa los cambios de código del Agent mode

    El código debería verse similar a lo siguiente:
    ```html
    <table class="table">
        <thead>
            <tr>
                <th>Image</th>
                <th>Name</th>
                <th>Description</th>
                <th>Price</th>
            </tr>
        </thead>
        <tbody>
            @foreach (var product in products)
            {
                <tr>
                    <td><img height="80" width="80" src="@($"{imagePrefix}/{product.ImageUrl}")" /></td>
                    <td>@product.Name</td>
                    <td>@product.Description</td>
                    <td>@product.Price</td>
                </tr>
            }
        </tbody>
    </table>
    ```

    El **ProductService** debería haber sido inyectado en la parte superior del archivo:
    ```html
    @inject ProductService ProductService
    ```

    El código debería haber sido actualizado en la parte inferior del archivo:
    ```cs
        @code {
        private List<Product>? products;
        private string imagePrefix = string.Empty;
    
        protected override async Task OnInitializedAsync()
        {
            // Simulate asynchronous loading to demonstrate streaming rendering
            await Task.Delay(500);
            imagePrefix = Configuration["ImagePrefix"]!;
            products = await ProductService.GetProducts();
        }
    }
    ```

1. [] Ejecuta la aplicación para ver tu nueva página de listado de productos.

1. [] Detén la depuración y cierra la aplicación

**Punto clave**: Copilot Agent puede generar implementaciones completas de funcionalidades basándose en tus descripciones en lenguaje natural, ahorrando un tiempo significativo de desarrollo.

---

[Atrás: Parte 04 - Usando instrucciones personalizadas](./part04-custom-instructions.md) | [Siguiente: Parte 06 - Usando Copilot Vision](./part06-copilot-vision.md)
