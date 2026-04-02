<!-- l10n-sync: source-file="part05-implementing-features.md" -->
# Parte 05: Implementando Funcionalidades com o Copilot Agent

Anteriormente utilizamos o Copilot Chat, que é ótimo para trabalhar com um arquivo individual ou fazer perguntas sobre nosso código. Porém, muitas atualizações necessitam de alterações em múltiplos arquivos em toda a base de código. Mesmo uma mudança aparentemente básica em uma página web provavelmente requer atualizar arquivos HTML, CSS, Razor e C#. O Copilot Agent permite que você modifique múltiplos arquivos de uma vez no seu projeto, se auto-corrige e pode executar comandos se autorizado, como instalar pacotes NuGet.

Com o Copilot Agent, você adicionará os arquivos que precisam ser atualizados ao contexto. Uma vez que você forneça o prompt, o Copilot Agent começará as atualizações em todos os arquivos no contexto. Ele também tem a capacidade de criar novos arquivos ou adicionar arquivos ao contexto conforme julgar apropriado.

Vamos adicionar a capacidade de ver uma lista de imagens na aplicação:

1. [] Abra o GitHub Copilot Chat no canto superior direito do Visual Studio e selecione **Open Chat Window** ou pressione `Ctrl+\+C` se o Copilot Chat não estiver aberto.

1. [] Mude para o modo **Agent**.

   ![Switch to agent mode](./images/1-agent.png)

1. [] No Visual Studio, abra um novo Copilot Chat com o ícone de chat **+**.

    ![New chat icon in VS copilot](./images/5-new-edits.png)

1. [] Na parte inferior do painel do GitHub Copilot Chat, selecione o modelo (padrão é "GPT-4o") na lista suspensa e selecione **Claude Opus 4.5** da lista de modelos disponíveis.

    ![Select Opus in Copilot](./images/5-select-sonnet.png)

1. [] Digite: `Implement a simple product listing page in Products.razor that fetches products from #ProductService and displays them in a simple list with product name, description, price, and image.`

    > NOTA: Você deve usar sua própria formulação ao gerar o prompt. Como destacado anteriormente, parte do exercício é se sentir confortável criando prompts para o GitHub Copilot. Uma dica importante é que sempre é bom fornecer mais orientação para garantir que você obtenha o código que está procurando.

    > NOTA: Se você for solicitado a **Enable Claude Opus 4.5 for all clients**, clique no botão **Enable**.

O Copilot Agent mode começa a implementar as sugestões de código!

## Revisando as alterações

Diferente dos nossos exemplos anteriores onde trabalhamos com um arquivo individual, agora estamos trabalhando com alterações em múltiplos arquivos — e talvez múltiplas seções de múltiplos arquivos. Felizmente, o Copilot Agent tem funcionalidades para ajudar a simplificar esse processo.

O GitHub Copilot irá propor as seguintes alterações na aplicação, incluindo a atualização do Products.razor e a adição de um Products.razor.css e possivelmente mais.

1. [] Revise as alterações de código do Agent mode

    O código deve ser semelhante ao seguinte:
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

    O **ProductService** deve ter sido injetado no topo do arquivo:
    ```html
    @inject ProductService ProductService
    ```

    O código deve ter sido atualizado na parte inferior do arquivo:
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

1. [] Execute a aplicação para ver sua nova página de listagem de produtos.

1. [] Pare a depuração e feche a aplicação

**Ponto-chave**: O Copilot Agent pode gerar implementações completas de funcionalidades com base nas suas descrições em linguagem natural, economizando tempo significativo de desenvolvimento.

---

[Voltar: Parte 04 - Usando Instruções Personalizadas](./part04-custom-instructions.md) | [Próximo: Parte 06 - Usando Copilot Vision](./part06-copilot-vision.md)
