# 🎯 ClickBonus API
 
API em **.NET 8** do **ClickBonus**, uma aplicação de cadastro de usuários para concorrer a bônus, construída com **ASP.NET Core Minimal API** e **Entity Framework Core (SQL Server)**.
 
Este repositório faz parte dos estudos de **Entity Framework Core avançado (Curso 3)** e traz a base da API: configuração do banco, contexto, entidade de usuário e documentação com Swagger.
 
> 🚧 **Status:** projeto em fase inicial. A estrutura de acesso a dados está pronta, e hoje a API expõe apenas o endpoint de teste `/hello`.
 
---
 
## ✨ O que existe hoje
 
- API **Minimal API** com documentação **Swagger** (em ambiente de desenvolvimento).
- Endpoint `GET /hello`, que retorna a mensagem `Click Bonus! Cadastra-se e concorra.`
- **DbContext** (`ClickBonusContext`) configurado para **SQL Server**, com a string de conexão lida do `appsettings.json`.
- Entidade **`Usuario`** (`Id`, `Nome`, `Email`, `Telefone`, `Cep`) mapeada como `DbSet<Usuario>`.
## 🧰 Tecnologias
 
| Tecnologia | Uso |
|---|---|
| C# e .NET 8 | Linguagem e plataforma |
| ASP.NET Core Minimal API | Construção dos endpoints |
| Entity Framework Core 8 + SQL Server | Acesso a dados (ORM) e banco |
| Swashbuckle (Swagger) | Documentação e testes da API |
 
## 📁 Estrutura do projeto
 
```
ClickBonus-API.sln
└── ClickBonus-API/
    ├── Program.cs                  # Configuração, DbContext, Swagger e endpoints
    ├── Context/ClickBonusContext.cs # DbContext do EF Core
    ├── Entidades/Usuario.cs        # Entidade Usuario
    ├── appsettings.json            # String de conexão (DefaultConnection)
    ├── Properties/launchSettings.json
    └── ClickBonus-API.http         # Arquivo de requisições de exemplo
```
 
## ✅ Pré-requisitos
 
- [.NET SDK 8.0](https://dotnet.microsoft.com/download/dotnet/8.0)
- SQL Server ou **SQL Server LocalDB** (instalado junto com o Visual Studio, no Windows)
- Ferramenta do EF Core:
```bash
dotnet tool install --global dotnet-ef
```
 
## 🚀 Como executar
 
### 1. Clone o repositório
 
```bash
git clone https://github.com/<seu-usuario>/clickbonus-avan-ef-core-curso3-record.git
cd clickbonus-avan-ef-core-curso3-record
```
 
### 2. Configure o banco de dados
 
A string de conexão fica em `ClickBonus-API/appsettings.json`, na chave `ConnectionStrings:DefaultConnection`. Por padrão, usa o **LocalDB** com o banco `ClickbonusX`:
 
```json
"ConnectionStrings": {
  "DefaultConnection": "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=ClickbonusX;Integrated Security=True;..."
}
```
 
Se usar outra instância do SQL Server, altere esse valor.
 
### 3. Crie o banco (Migrations)
 
O repositório ainda **não possui migrations**. Para criar a tabela de usuários a partir da entidade:
 
```bash
cd ClickBonus-API
dotnet ef migrations add Inicial
dotnet ef database update
```
 
### 4. Execute a API
 
```bash
dotnet run --launch-profile https
```
 
- Swagger: `https://localhost:7161/swagger`
- HTTP: `http://localhost:5143/swagger`
Teste o endpoint:
 
```bash
curl http://localhost:5143/hello
# "Click Bonus! Cadastra-se e concorra."
```
 
## 📡 Endpoints
 
| Método | Rota | Descrição |
|---|---|---|
| `GET` | `/hello` | Mensagem de boas-vindas (teste da API) |
 
## 🗄️ Modelo de dados
 
**Usuario**
 
| Campo | Tipo |
|---|---|
| `Id` | `int` |
| `Nome` | `string?` |
| `Email` | `string?` |
| `Telefone` | `string?` |
| `Cep` | `string?` |
 
## 🗺️ Próximos passos
 
- [ ] Criar a migration inicial e versioná-la no repositório.
- [ ] Implementar os endpoints de **usuários** (cadastro, listagem, consulta, atualização e exclusão).
- [ ] Usar *records* para os DTOs de entrada e saída.
- [ ] Validar os dados (e-mail, telefone e CEP) e impedir e-mails duplicados.
- [ ] Atualizar o `ClickBonus-API.http`, que ainda aponta para `/weatherforecast` (rota que não existe nesta API).
- [ ] Adicionar testes automatizados.

## 📄 Licença
 
Defina aqui a licença do projeto (por exemplo, [MIT](https://opensource.org/licenses/MIT)).
 
---
 
Feito com 💙 durante os estudos de **Entity Framework Core**.
 
