# Guia Completo do Projeto .NET 8 🚀

Este documento apresenta, de forma profissional e acolhedora, tudo o que você precisa para instalar o .NET 8 (versão 8.0.417), configurar o ambiente e executar o projeto localmente. Respire fundo, prepare seu terminal favorito e vamos nessa! 😄

## 1. Visão Geral
- **Stack principal:** ASP.NET Core 8.0 (SDK 8.0.417)
- **Objetivo:** API moderna e performática pronta para produção
- **Estrutura-chave:** `dotnet8-api-project.csproj`, `global.json`, `appsettings*.json`

## 2. Pré-requisitos Essenciais
1. **Sistema Operacional**: Windows 10/11, macOS Ventura+, ou distribuições Linux suportadas.
2. **Acesso administrativo** para instalar o SDK.
3. **Conectividade** para baixar dependências via NuGet.

## 3. Instalação do .NET 8 (8.0.417)

### 3.1 Checar instalação atual
```bash
dotnet --info
```
Se a versão listada não for `8.0.417`, siga um dos caminhos abaixo.

### 3.2 Instalar via Winget (Windows)
```bash
winget install --id Microsoft.DotNet.SDK.8 --version 8.0.417
```

### 3.3 Instalar manualmente
1. Acesse https://dotnet.microsoft.com/en-us/download/dotnet/8.0
2. Baixe o instalador correspondente ao seu SO.
3. Execute o instalador e conclua o wizard.

### 3.4 Validar pós-instalação
```bash
dotnet --version
# Saída esperada: 8.0.417
```

## 4. Configuração do Projeto

### 4.1 Arquivo `global.json`
Garante que a versão correta do SDK seja usada:

```json
{
	"sdk": {
		"version": "8.0.417"
	}
}
```

### 4.2 Restaurar dependências
```bash
dotnet restore
```

### 4.3 Construir o projeto
```bash
dotnet build
```

## 5. Executando a Aplicação 🎯

### 5.1 Execução padrão (perfil Development)
```bash
dotnet run
```
- A saída do console mostrará a URL base (ex.: http://localhost:5000).
- Use ferramentas como `curl`, Postman ou seu navegador favorito para validar os endpoints.

### 5.2 Execução com URL customizada
```bash
dotnet run --urls "https://localhost:7140;http://localhost:5180"
```

### 5.3 Publicação para produção
```bash
dotnet publish -c Release -o ./publish
```
O diretório `publish` conterá os artefatos prontos para deploy.

## 6. Dicas de Configuração 🔧
- **Variáveis de ambiente**: defina `ASPNETCORE_ENVIRONMENT=Development` (ou `Production`) conforme necessário.
- **Logs**: ajuste níveis em `appsettings.Development.json` para debugar comportamentos específicos.
- **Hot Reload**: use `dotnet watch run` para ciclos rápidos de feedback.

## 6.1 Configuração do xUnit 3 para Testes
Para configurar um projeto de testes usando xUnit 3, siga os passos abaixo:
```bash
dotnet new search xunit3
dotnet new install xunit.v3.templates
dotnet new xunit3 -n PlaywrightTestsXunit3
dotnet tool install --global PowerShell
```

## 7. Troubleshooting 🙌
- **SDK incorreto**: confirme `dotnet --list-sdks` e remova versões conflitantes, se necessário.
- **Porta ocupada**: altere `--urls` ou finalize processos que estejam usando a porta.
- **Certificado HTTPS**: rode `dotnet dev-certs https --trust` (Windows/macOS) caso encontre erros de certificado.

Pronto! Agora você está preparado para instalar, configurar e executar o projeto com confiança. Qualquer dúvida, abra uma issue ou entre em contato com o time. Boa codificação! 💙
