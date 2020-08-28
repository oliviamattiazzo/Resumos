# Aula 01 - Introdução

Observação: esse resumo foi elaborado no dia 12/01/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Sem Entity
* Scripts precisam ser mantidos nos arquivos do projeto
* DAO -> Data Access Object
    * Isola a responsabilidade do banco
    * Padrão de arquitetura
    * SQLs montados na unha, em variáveis string
* ADO.NET
    * Providers para cada banco de dados (MySQL, Oracle, SQL Server)

### → Entity Framework
* Lida com o "trabalho sujo" das mudanças do BD

### :warning: Entity Framework é um **ORM**
* **ORM** = Mapeamento Objeto Relacional
* **Vantagens:**
    * Maior *produtividade* do desenvolvedor
        * Muita abstração do código de persistência
    * Maior facilidade de *refatoração*
        * Blindagem do trabalho sujo
    * Não há preocupação com o *SQL*
        * Somente intervenções em casos específicos

### → Como instalar
* Via console do NuGet:

```csharp 
Install-Package Microsoft.EntityFrameworkCore.SqlServer -Version[XX]
```