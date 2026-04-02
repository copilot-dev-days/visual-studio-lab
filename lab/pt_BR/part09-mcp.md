<!-- l10n-sync: source-file="part09-mcp.md" -->
# Parte 09: MCP Servers

Model Context Protocol (MCP) é um protocolo aberto que padroniza como aplicações fornecem contexto para grandes modelos de linguagem (LLMs). MCP servers estendem as capacidades do GitHub Copilot conectando-o a ferramentas e serviços externos, dando-lhe acesso a dados em tempo real e a capacidade de realizar ações.

Nesta parte, você aprenderá como adicionar MCP servers ao Visual Studio e usá-los para obter informações sobre a otimização da sua aplicação.

## Adicionando MCP Servers da Galeria

O Visual Studio fornece uma galeria de MCP servers pré-configurados que você pode facilmente adicionar ao seu projeto.

Para ver suas ferramentas existentes e MCP servers instalados:
1. [] Abra a janela do Copilot Chat clicando no ícone do GitHub Copilot e selecionando **Open Chat Window** ou pressione `Ctrl+\+C`.
1. [] Clique no ícone **Tools** na parte inferior da janela de chat para abrir a configuração do MCP server.

   ![MCP Tools icon](./images/9-mcp-tools.png)
1. Ferramentas integradas e de MCP servers aparecerão.
1. Clique no ícone **+** para adicionar um novo MCP server.
1. 
   ![Add MCP server](./images/9-add-mcp-server.png)
1. Especifique o seguinte
1. **Destination**: Solution
1. **Server Id**: `github`
1. **Type**: HTTP
1. **URL**: https://api.githubcopilot.com/mcp/

   ![GitHub MCP server configuration](./images/9-github-mcp-server.png)


1. O GitHub MCP requer autenticação. No **Solution Explorer**, expanda **SolutionItems** e abra **.mcp.json**, e você verá uma mensagem **Authentication required**. Clique nela e clique em Authenticate. Após isso, você verá que está online e pronto para uso.
   ![GitHub MCP authentication](./images/9-github-mcp-authentication.png)


O Visual Studio 2026 possui uma galeria integrada de MCP para ajudá-lo a instalar facilmente MCP servers:

1. [] No Visual Studio 2026, vá para **Extensions -> MCP Registries...** para abrir a janela de gerenciamento de MCP servers.
 
   ![MCP Registries menu](./images/9-mcp-registries-menu.png)

1. [] Navegue pelos MCP servers existentes na galeria.

> [!TIP]
> MCP servers podem fornecer acesso a documentação, APIs e outros serviços que podem ajudar o Copilot a dar respostas mais precisas e contextuais.



## Usando MCP Servers para Obter Informações

Agora que você tem os MCP servers do Microsoft Learn e do GitHub instalados, vamos usá-los para obter informações sobre a otimização do carregamento de recursos na aplicação.

1. [] No Copilot Chat, mude para o modo **Agent**. 
1. [] Certifique-se de que o MCP server do Microsoft Learn está selecionado como ferramenta ativa. Se você não o vir, clique em uma nova sessão de chat ou alterne os modos:
  ![Select MCP server](./images/9-select-mcp-server.png)
1. [] Digite o seguinte prompt: `Using the Microsoft Learn docs mcp, what are the best practices for optimizing image loading and asset delivery in a Blazor Server application?`
1. [] Revise a resposta do Copilot, que agora tem acesso à documentação mais recente da Microsoft através do MCP server.

## Criando GitHub Issues com MCP

O GitHub MCP server permite que o Copilot interaja com seu repositório GitHub. Vamos usá-lo para criar issues para melhorias que queremos fazer na aplicação.

1. [] Certifique-se de que o GitHub MCP server está selecionado como ferramenta ativa no Copilot Chat.
1. [] Na mesma sessão de chat, digite: `Based on the asset optimization recommendations, create 3 GitHub issues for improving the TinyShop application's performance.`

   > NOTA:
   > O Copilot usará o GitHub MCP server para criar as issues diretamente no seu repositório. Pode ser solicitado que você autorize a ação.

1. [] Revise as issues que o Copilot propõe criar.
1. [] Aprove a criação das issues quando solicitado.
1. [] Navegue até seu repositório GitHub para verificar se as issues foram criadas.

**Ponto-chave**: MCP servers estendem as capacidades do GitHub Copilot conectando-o a serviços externos e documentação. Isso permite que o Copilot forneça informações mais precisas e atualizadas e realize ações como criar GitHub issues diretamente da interface de chat.

---

[Voltar: Parte 08 - Descrições de Resumo de Commit](./part08-commit-summary-descriptions.md) | [Próximo: Parte 10 - Planning Mode no Agent](./part10-planning-mode.md)
