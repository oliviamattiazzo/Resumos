# Aula 03 - Como o Entity monta o SQL?

Observação: esse resumo foi elaborado no dia 19/01/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → [Classe] DbContext
* Classe base de toda a API do Entity
* **[Propriedade] .ChangeTracker**
    * Responsável por mapear todas as mudanças ocorridas em uma instância do contexto
    * **[Método] .Entries()**
        * Lista de todas as entidades que estão sendo gerenciadas naquele momento, naquele contexto
        ```csharp
        contexto.ChangeTracker.Entries();
        ```
        * **[Propriedade] .State**
            * Registra o estado da entidade
            * Se a entidade mudou o estado, o método .SaveChanges() precisa agir
            ```csharp
            e.State;
            ```

### → Como o .ChangeTracker sabe que, quando uma propriedade foi alterada, ele deve fazer um UPDATE no banco?
* O Entity guarda um "snapshot" dos valores do objeto por padrão
* Cria-se uma entrada no ChangeTracker quando o objeto começa a ser monitorado, passando seu valor como argumento
* Chama o método .DetectChanges() ao executar o .SaveChanges()
    * **.DetectChanges()** → verifica diferenças entre os valores atuais e originais

:warning: É possível desligar o monitoramento automático através da propriedade *AutoDetectChangesEnabled*
* Quando fazer? → Em ocasiões de gravações massivas de objetos que podem gerar impacto na performance

### → Para logar os SQLs montados pelo Entity
1. Provedor de serviços
```csharp
using Microsoft.EntityFramework.Infrastrucutre;

var serviceProvider = contexto.GetInfrastructure<IServiceProvider>();
```
2. Pegar serviço de Logger
```csharp
using Microsoft.Extensions.Logging;
using Microsoft.Extensions.DependencyInjection;

var loggerFactory = serviceProvider.GetService<ILoggerFactory>();
```
3. Fornecimento de um logger específico para transferir o logger do Entity para o logger do programa
```csharp
loggerFactory.AddProvider(SqlLoggerProvider.Create());
```
4. Ajeitar classe provider do logger
```csharp
SqlLoggerProvider => altos códigos
```

### → Estados do Entity Framework
* Unchanged
* Modified
    * Só acontrece quando objeto está sendo monitorado
* Added
    ```csharp
    .Add(produto);
    ```
* Deleted
    ```csharp
    .Remove(produto);
    ```
* Detached
    ```csharp
    .Add(produto)
    .Remove(produto)
    var entry = contexto.Entry(produto);
    entry.State;
    ```

### → Esquema de estados do Entity Framework
![Esquema de estados do Entity Framework](https://github.com/oliviamattiazzo/Resumos/blob/master/EntityFramework/Esquema_Estados_Entity.png)