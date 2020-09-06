# Aula 04 - Sincronizando o banco de dados com o modelo de classes

Observação: esse resumo foi elaborado no dia 26/01/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → DDL
* Data Definition Language
* Subconjunto da linguagem SQL
* **Exemplo:** CREATE TABLE

### → DML
* Data Manipulation Language
* Outro subconjunto do SQL
* **Exemplo:** INSERT, DELETE, UPDATE, SELECT

### → Alterei a classe que representa minha tabela. Como alterar o BD automaticamente?
**RESPOSTA:** Migrations!
* Para instalar pacote do Migrations (via console NuGet)
```csharp
Install-Package Microsoft.EntityFrameworkCore.Tools
```
* Para receber informações sobre o pacote (também via console NuGet)
```csharp
Get-Help EntityFramework
```

### → Estratégia para migração do Entity Framework
1. Registrar a migração
    * **Add-Migration** [nome]
    * Exemplo:
    ```csharp
    Add-Migration Unidade
    ```
    * Criação pasta "Migrations"
        * Snapshot.cs
        * [timestamp_nome].cs
            * Herda *Migration* → API que fará a sincronização
            * 2 métodos
                * **Up** → atualiza para versão mais recente
                * **Down** → volta para uma versão anterior
            
2. Existem 2 maneiras
    * **Script-Migration**
        * Gera um arquivo de script com o DDL que vai atualizar o banco
        * Cenário mais utilizado quando existe uma equipe de BD separada da equipe de desenvolvimento
    * **Update-Database**
        * Entity pega a nova versão registrada e executa diretamente no banco de dados
        * Listar tudo que acontece "por baixo dos panos"
        ```csharp
        Update-Database -Verbose
        ```
        * Executar uma migration específica
        ```csharp
        Update-Database Inicial
        ```

:eight_spoked_asterisk: Tabela **_EFMigrationsHistory** registra o histórico de versões

### → Em caso de erro, para desfazer uma migração:
1. Excluir a tabela _EFMigrationsHistory
2. Excluir pasta "Migrations"

:warning: Antes de fazer uma migração com alterações, gerar uma primeira versão com o banco "original"
```csharp
Add-Migration Inicial
```

:eight_spoked_asterisk: Cada Update-Database **adiciona uma linha na tabela _EFMigrationsHistory**, registrando a versão

:eight_spoked_asterisk: É possível fazer com que a **própria aplicação cuide da migração** das versões
* Método de extensão **Migrate** (propriedade *Database*, classe DbContext)
    * Propriedade **Database** → representa a instância do BD apontado pelo contexto da sua aplicação
        * Expõe métodos para gerenciar o banco do contexto
```csharp
using (contexto) {
    contexto.Database.Migrate();
}
```
* Método Migrate só pode ser usado em BDs relacionais