<!-- l10n-sync: source-file="part01-code-completion.md" -->
# Parte 01: Code Completion com Ghost Text

Nesta seção, você usará o Code Completion do GitHub Copilot para implementar endpoints da API.

> IMPORTANTE: Para este exercício, **NÃO** copie e cole o trecho de código fornecido, mas sim digite-o manualmente. Isso permitirá que você experimente o Code Completion como faria se estivesse codificando no seu trabalho. Você provavelmente verá que só precisa digitar alguns caracteres antes que o GitHub Copilot comece a sugerir o restante.

1. [] Pare a depuração da aplicação se ela estiver em execução.


1. [] No Solution Explorer, no projeto **Products**, abra **Endpoints/ProductEndpoints.cs** - ele terá um único endpoint implementado.

   > Nota: O GitHub Copilot não dará sugestões de código durante a depuração.
   
1. [] Vamos implementar um novo **MapGet** para obter detalhes do produto para um **id** específico. Mova o cursor e clique na linha 20 abaixo do endpoint **/** existente. Uma sugestão de texto pode aparecer ou digite:
   ```csharp
   g
   ```
1. [] Aguarde as sugestões de Ghost Text aparecerem (texto em cinza).
;
   ![Code suggestions](./images/1-ghost-text.png)

1. [] Pressione Tab para aceitar a sugestão ou continue digitando para obter sugestões mais específicas.

1. [] A partir daí, Next Edit Suggestions (NES) ou sugestões adicionais de Ghost Text aparecerão. 

   ![NES showing up](./images/1-nes.png)

1. [] Agora podemos implementar os seguintes endpoints usando o GitHub Copilot:
   - POST para criar um novo produto
   - PUT para atualizar um produto
   - DELETE para remover um produto

   - Podemos continuar usando sugestões OU podemos abrir o GitHub Copilot Chat e trabalhar com Agent mode:
     - Abra o GitHub Copilot Chat no canto superior direito do Visual Studio e selecione **Open Chat Window** ou pressione `Ctrl+\+C` se o Copilot Chat não estiver aberto.
     - Mude para o modo **Agent**.
     - ![Switch to agent mode](./images/1-agent.png)]
     - Peça ao agente: `Can you implement the rest of the endpoints for the Product API and also implement the ProductService to call these new endpoints in the Store project?`

   O código final em **ProductEndpoints.cs** deve ser semelhante a:

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

   No projeto **Store**, no Solution Explorer, abra **Services/ProductService.cs**, o código deve ser semelhante a:

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

   > NOTA: Como LLMs são probabilísticos, não determinísticos, o código exato gerado pode variar. O exemplo acima é representativo. Se seu código for diferente, tudo bem, desde que funcione!

1. Clique em **Keep** após revisar as alterações na janela do GitHub Copilot Chat.

1. [] Volte para **ProductEndpoints.cs** e tente alterar o nome da variável **id** para `productId` no novo método **MapGet** e veja as Next Edit Suggestions ajudando.

   ![NES suggestions more](./images/1-nes-2.png)

1. [] Tente usar a geração de documentação:
   - Digite `///` acima de um método para gerar documentação XML no **MapProductEndpoints**. Isso também pode ser acionado com `Alt+/` para inline e depois digitando **/** que exibirá uma lista de comandos. A geração de documentação aparecerá como Ghost Text e pode ser aceita com `Tab`.

   ![documentation generation by Copilot](./images/1-docs.png)

1. [] Teste sua implementação:
   - Execute o projeto AppHost.
   - Teste seus novos endpoints acessando **https://localhost:7130/api/Product/1**

1. [] Pare a depuração e feche a aplicação

---

[Voltar: Parte 00 - Explorando a Base de Código com GitHub Copilot Chat](./part00-exploring-codebase.md) | [Próximo: Parte 02 - Melhorando a UI com Inline Chat](./part02-enhancing-ui.md)
