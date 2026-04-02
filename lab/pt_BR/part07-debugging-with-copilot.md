<!-- l10n-sync: source-file="part07-debugging-with-copilot.md" -->
# Parte 07: Depuração com o Copilot

Nesta seção, você aprenderá como usar o Copilot para depurar uma exceção na sua aplicação.

1. [] Depure o projeto **AppHost** se ainda não estiver depurando, e abra a **store** pelo .NET Aspire dashboard.
1. [] Clique no botão **Go to About** no menu de navegação.
1. [] Observe que uma exceção ocorre e a aplicação trava.
1. [] Pressione a opção **Analyze with Copilot** no pop-up.

    ![Pop up for exception with Analyze with Copilot option](./images/7-ask-copilot-exception.png)

1. [] Revise como o Copilot traz informações do depurador, incluindo stack traces e estados de variáveis.
1. [] Observe como o Copilot recomenda uma correção para o problema ou fornece sugestões de código para resolvê-lo.

**Ponto-chave**: O Copilot pode auxiliar no diagnóstico e correção de exceções analisando informações do depurador e fornecendo recomendações acionáveis.

## Usando Watch Windows e Visualizers

Nesta subseção, você aprenderá como usar o Copilot para analisar variáveis usando watch windows e visualizers.

1. [] Abra o arquivo **Products.razor** novamente no projeto **Products**.
1. [] Adicione um breakpoint no final do método **OnInitializedAsync**.
1. [] Depure o **TinyShop.AppHost** e abra a **store** pelo .NET Aspire dashboard, e navegue até a página **Products**.
1. [] Quando o breakpoint for atingido, passe o mouse sobre a variável **imagePrefix**.
1. [] Pressione o botão **Copilot** para analisar a variável **imagePrefix**.

    ![Copilot button on variable](./images/7-inspect-variable.png)

    >Nota: você também pode ver isso nas janelas Locals ou watch

1. [] Observe como o Copilot fornece informações detalhadas sobre a variável, incluindo seu valor e possíveis problemas.
1. [] Passe o mouse sobre a coleção **products** e clique no botão **View** com o ícone de lupa.

    ![View button on products](./images/7-view-products.png)

1. [] Use o visualizer para inspecionar o conteúdo da coleção **products**.
1. [] Clique no botão Generate expression e, em linguagem natural, digite: `Products that have the name outdoor in them and are under 40 dollars`
1. [] Observe como o Copilot gera a expressão apropriada automaticamente.

    ![Generate expression for visualizer](./images/7-visualizer-sparkle.png)

**Ponto-chave**: O Copilot pode aprimorar a depuração fornecendo insights detalhados sobre variáveis através de watch windows e visualizers. O Copilot pode simplificar tarefas complexas de depuração gerando expressões e consultas LINQ com base em entrada em linguagem natural.

---

[Voltar: Parte 06 - Usando Copilot Vision](./part06-copilot-vision.md) | [Próximo: Parte 08 - Descrições de Resumo de Commit](./part08-commit-summary-descriptions.md)
