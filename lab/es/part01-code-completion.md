<!-- l10n-sync: source-file="part01-code-completion.md" -->
# Parte 01: Code Completion con Ghost Text

En esta sección, usarás la función de Code Completion de GitHub Copilot para implementar endpoints de API.

> IMPORTANTE: Para este ejercicio, **NO** copies y pegues el fragmento de código proporcionado, sino escríbelo manualmente. Esto te permitirá experimentar Code Completion como lo harías al programar en tu escritorio. Es probable que solo tengas que escribir unos pocos caracteres antes de que GitHub Copilot comience a sugerir el resto.

1. [] Detén la depuración de la aplicación si está ejecutándose actualmente.


1. [] En el Solution Explorer, en el proyecto **Products**, abre **Endpoints/ProductEndpoints.cs** - tendrá un único endpoint implementado.

   > Nota: GitHub Copilot no dará sugerencias de código mientras se está depurando.
   
1. [] Implementemos un nuevo **MapGet** para obtener los detalles de un producto por un **id** específico. Mueve el cursor y haz clic en la línea 20 debajo del endpoint **/** existente. Puede aparecer una sugerencia de texto o escribe:
   ```csharp
   g
   ```
1. [] Espera a que aparezcan las sugerencias de Ghost Text (texto en gris).
;
   ![Code suggestions](./images/1-ghost-text.png)

1. [] Presiona Tab para aceptar la sugerencia o continúa escribiendo para obtener sugerencias más específicas.

1. [] A partir de ahí aparecerán Next Edit Suggestions (NES) o sugerencias adicionales de Ghost Text.

   ![NES showing up](./images/1-nes.png)

1. [] Ahora podemos implementar los siguientes endpoints usando GitHub Copilot:
   - POST para crear un nuevo producto
   - PUT para actualizar un producto
   - DELETE para eliminar un producto

   - Podemos continuar usando sugerencias O podríamos abrir GitHub Copilot Chat y trabajar con Agent mode:
     - Abre GitHub Copilot Chat en la esquina superior derecha de Visual Studio y selecciona **Open Chat Window** o presiona `Ctrl+\+C` si el chat de Copilot no está abierto.
     - Cambia a modo **Agent**.
     - ![Switch to agent mode](./images/1-agent.png)]
     - Pregunta al agente: `Can you implement the rest of the endpoints for the Product API and also implement the ProductService to call these new endpoints in the Store project?`

   El código final en **ProductEndpoints.cs** debería verse similar a:

   ```csharp
   group.MapGet("/", async (ProductDataContext db) =>
   {
      return await db.Product.ToListAsync();
   })
   .WithName("GetAllProducts")
   .Produces<List<Product>>(StatusCodes.Status200OK);

   group.MapGet("/{id}", async  (int id, ProductDataContext db) =>
   {
      return await db.Product.AsNoTracking()
            .FirstOrDefaultAsync(model => model.Id == id)
            is Product model
               ? Results.Ok(model)
               : Results.NotFound();
   })
   .WithName("GetProductById")
   .Produces<Product>(StatusCodes.Status200OK)
   .Produces(StatusCodes.Status404NotFound);

   group.MapPut("/{id}", async  (int id, Product product, ProductDataContext db) =>
   {
      var affected = await db.Product
            .Where(model => model.Id == id)
            .ExecuteUpdateAsync(setters => setters
            .SetProperty(m => m.Id, product.Id)
            .SetProperty(m => m.Name, product.Name)
            .SetProperty(m => m.Description, product.Description)
            .SetProperty(m => m.Price, product.Price)
            .SetProperty(m => m.ImageUrl, product.ImageUrl)
            );

      return affected == 1 ? Results.Ok() : Results.NotFound();
   })
   .WithName("UpdateProduct")
   .Produces(StatusCodes.Status404NotFound)
   .Produces(StatusCodes.Status204NoContent);

   group.MapPost("/", async (Product product, ProductDataContext db) =>
   {
      db.Product.Add(product);
      await db.SaveChangesAsync();
      return Results.Created($"/api/Product/{product.Id}",product);
   })
   .WithName("CreateProduct")
   .Produces<Product>(StatusCodes.Status201Created);

   group.MapDelete("/{id}", async  (int id, ProductDataContext db) =>
   {
      var affected = await db.Product
            .Where(model => model.Id == id)
            .ExecuteDeleteAsync();

      return affected == 1 ? Results.Ok() : Results.NotFound();
   })
   .WithName("DeleteProduct")
   .Produces<Product>(StatusCodes.Status200OK)
   .Produces(StatusCodes.Status404NotFound);
   ```

   En el proyecto **Store** en el Solution Explorer, abre **Services/ProductService.cs**, el código debería verse similar a:

   ```cs
   using DataEntities;
   using System.Text.Json;
   
   namespace Store.Services;
   
   public class ProductService
   {
      HttpClient httpClient;
      public ProductService(HttpClient httpClient)
      {
         this.httpClient = httpClient;
      }
      public async Task<List<Product>> GetProducts()
      {
         List<Product>? products = null;
         var response = await httpClient.GetAsync("/api/Product");
         if (response.IsSuccessStatusCode)
         {
               var options = new JsonSerializerOptions
               {
                  PropertyNameCaseInsensitive = true
               };
   
               products = await response.Content.ReadFromJsonAsync(ProductSerializerContext.Default.ListProduct);
         }
   
         return products ?? new List<Product>();
      }
   
      public async Task<Product?> GetProductById(int id)
      {
         var response = await httpClient.GetAsync($"/api/Product/{id}");
         if (response.IsSuccessStatusCode)
         {
               return await response.Content.ReadFromJsonAsync<Product>(ProductSerializerContext.Default.Product);
         }
         return null;
      }
   
      public async Task<bool> CreateProduct(Product product)
      {
         var response = await httpClient.PostAsJsonAsync("/api/Product", product, ProductSerializerContext.Default.Product);
         return response.IsSuccessStatusCode;
      }
   
      public async Task<bool> UpdateProduct(int id, Product product)
      {
         var response = await httpClient.PutAsJsonAsync($"/api/Product/{id}", product, ProductSerializerContext.Default.Product);
         return response.IsSuccessStatusCode;
      }
   
      public async Task<bool> DeleteProduct(int id)
      {
         var response = await httpClient.DeleteAsync($"/api/Product/{id}");
         return response.IsSuccessStatusCode;
      }
   }
   ```

   > NOTA: Debido a que los LLMs son probabilísticos, no determinísticos, el código exacto generado puede variar. Lo anterior es un ejemplo representativo. Si tu código es diferente, está bien siempre que funcione.

1. Haz clic en **Keep** después de revisar los cambios en la ventana de GitHub Copilot Chat.

1. [] Regresa a **ProductEndpoints.cs**, e intenta cambiar el nombre de la variable **id** a `productId` en el nuevo método **MapGet** y observa cómo Next Edit Suggestions te ayuda.

   ![NES suggestions more](./images/1-nes-2.png)

1. [] Prueba la generación de documentación:
   - Escribe `///` encima de un método para generar documentación XML en el **MapProductEndpoints**; esto también se puede invocar con `Alt+/` para inline y luego escribiendo **/** que mostrará una lista de comandos. La generación de documentación aparecerá como Ghost Text y se puede aceptar con `Tab`.

   ![documentation generation by Copilot](./images/1-docs.png)

1. [] Prueba tu implementación:
   - Ejecuta el proyecto AppHost.
   - Prueba tus nuevos endpoints yendo a **https://localhost:7130/api/Product/1**

1. [] Detén la depuración y cierra la aplicación

---

[Atrás: Parte 00 - Explorando el código fuente con GitHub Copilot Chat](./part00-exploring-codebase.md) | [Siguiente: Parte 02 - Mejorando la UI con Inline Chat](./part02-enhancing-ui.md)
