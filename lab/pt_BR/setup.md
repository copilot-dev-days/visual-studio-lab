<!-- l10n-sync: source-file="setup.md" -->
# Configuração do Workshop

Para completar este workshop, você precisará do Visual Studio 2026, do .NET 10 SDK e de uma conta GitHub com acesso ao GitHub Copilot.

## Pré-requisitos

Antes de começar, certifique-se de que você tem:

- **Visual Studio 2026** com a extensão GitHub Copilot instalada
- **.NET 10 SDK** instalado
- **Conta GitHub** com uma das seguintes opções:
  - [GitHub Copilot Free](https://github.com/features/copilot) - Nível gratuito com uso limitado
  - [GitHub Copilot Pro](https://github.com/features/copilot) - Acesso completo (teste gratuito de 30 dias disponível)
  - GitHub Copilot através da sua organização

> [!TIP]
> Se você ainda não tem o GitHub Copilot, pode [se inscrever no Copilot Free](https://github.com/features/copilot) ou iniciar um [teste gratuito do Copilot Pro](https://github.com/github-copilot/signup).

## Instalar a Extensão .github + MCP

Antes de começarmos, vamos instalar a extensão .github + MCP para o Visual Studio. Esta extensão fornece acesso aos GitHub MCP servers que usaremos mais adiante no laboratório.

1. [] Abra o Visual Studio 2026
1. [] Vá para **Extensions -> Manage Extensions**
1. [] Pesquise por **.github + MCP** na caixa de busca
1. [] Clique em **Install** na extensão **.github + MCP** de Mads Kristensen
1. [] Reinicie o Visual Studio se solicitado

> [!TIP]
> Você também pode instalar esta extensão pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.GitHubNode). A extensão .github + MCP é importante porque fornece o runtime Node.js necessário para alguns MCP servers, que você usará na Parte 9 deste laboratório.

## Entrar no GitHub Copilot

1. [] Abra seu navegador e acesse `https://github.com`.
1. [] Entre com sua conta GitHub ou crie uma nova conta se você não tiver uma.
1. [] Abra o Visual Studio 2026.
1. [] Selecione **Continue without code**. Se solicitado para fazer login, você pode clicar em Close.
1. [] Clique no ícone do Copilot na barra superior (lado esquerdo, próximo à caixa de busca).
1. [] Clique em **Sign in to use Copilot**.
1. [] Uma janela do navegador será aberta solicitando que você entre no GitHub e autorize o Visual Studio e o Copilot. Complete o login e clique em **Authorize** quando solicitado.
1. [] Quando o navegador mostrar a confirmação, clique em **Open** para retornar ao Visual Studio.
1. [] Após a configuração, você deverá ver a aba **GitHub Copilot Walkthrough** e o botão do Copilot deverá estar verde.

> [!NOTE]
> Para os exercícios práticos que criam ou modificam dados do repositório via Cloud Agent (Parte 12), você precisará fazer um fork do repositório do laboratório na sua própria conta. Isso dá ao Cloud Agent permissões para operar no seu fork.

## Ativar Configurações do Copilot

1. [] Certifique-se de que Code Completions e Next Edit Suggestions estão habilitados:
   - Vá para as configurações de Code Completions no Visual Studio em **Tools -> Options -> Text Editor -> Code Completions**
   - Certifique-se de que **Copilot Completions** está marcado.
   - Certifique-se de que **Copilot Next Edit Suggestions** está marcado.

   ![](./images/0-enable-nes.png)

1. [] Vá para **Tools -> Options -> GitHub -> Copilot -> Copilot Chat** e certifique-se de que as seguintes configurações estão habilitadas:
   - **Enable Planning**
   - **Enable View Plan Execution**
   - **Enable Copilot Coding agent (Preview)**


## Clonar o Repositório do Laboratório

Para a experiência completa — especialmente se você planeja delegar tarefas para Cloud Agents ou permitir que o Copilot crie issues e faça push de alterações — faça um fork do repositório para sua própria conta GitHub e clone seu fork.

1. [] No seu navegador, acesse `https://github.com/copilot-dev-days/visual-studio-lab` e clique em **Fork** para criar um fork na sua conta GitHub.
1. [] No Visual Studio, clique em **File -> Clone Repository**.
1. [] Insira a URL do seu fork (por exemplo `https://github.com/<your-username>/visual-studio-github-copilot-lab`) e pressione **Clone**.

Se você preferir não fazer fork, ainda pode clonar o repositório upstream diretamente:

1. [] No Visual Studio, clique em **File -> Clone Repository**.
1. [] Insira `https://github.com/copilot-dev-days/visual-studio-lab` e pressione **Clone**.

O código agora está aberto no Visual Studio. Fique à vontade para explorar ou pule para a próxima seção para iniciar a aplicação.

## Iniciar a Aplicação

1. [] Abra o **Solution Explorer** pelo menu **View -> Solution Explorer**.
1. [] Defina o **TinyShop.AppHost** como projeto de inicialização, se ainda não estiver, clicando com o botão direito em **TinyShop.AppHost** e selecionando **Set as Startup Project**. Inicie o projeto com F5 ou **Debug -> Start Debugging** no menu.

    O .NET Aspire AppHost iniciará duas aplicações e o .NET Aspire Dashboard:

    - A aplicação backend .NET em **https://localhost:7130/api/Product**
    - A aplicação frontend Blazor em **https://localhost:7085** - Você pode ver a aplicação abrindo essa URL pelo dashboard

1. [] Pare a depuração e feche a aplicação.

## Resumo e Próximos Passos

Você agora configurou seu ambiente e clonou o repositório que usará no restante do workshop. Vamos começar a explorar o GitHub Copilot!

---

[Próximo: Parte 00 - Explorando a Base de Código](./part00-exploring-codebase.md)
