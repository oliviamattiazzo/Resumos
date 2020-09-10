# Aula 08 - Recuperando objetos relacionados

Observação: esse resumo foi elaborado no dia 08/05/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:eight_spoked_asterisk: Comportamento de não recuperar entidades relacionadas é padrão no Entity Framework
* Caso esse não fosse o padrão, poderia haver problemas de performance (busca traria para a memória todas as entidades relacionadas)
* **Solução:** explicitar ao Entity quais entidades relacionadas queremos trazer

:eight_spoked_asterisk: Para fazer o `JOIN` via Linq, usar método `.Include()` e/ou `.ThenInclude()`
* Relacionamentos N:N
* **Exemplo:**
```csharp
contexto
    .Promocoes
    .Include(p => p.Produtos)
    .ThenInclude(pp => pp.Produto)
    .FirstOrDefault();
```

:warning: Método `Include()` possui outra sobrecarga
* String com o nome da propriedade de navegação a ser incluída no `JOIN`
* **Vantagem:** não é preciso usar o `.ThenInclude()` para continuar a navegação
```csharp
var lista = contexto.Clientes.Include("Contas.Conta");
```
* **Desvantagem:** se o nome da propriedade mudar, vai dar trabalho

### → Relacionamento 1:1
* `.Include()` corresponde à `LEFT JOIN` quando a propriedade não é obrigatória

### → Relacionamento 1:N
* Garantir que haja uma propriedade que possibilite a navegação pelo N

:warning: `.Where()` não pode ser usado depois de `.Include()`
* **Solução:** há outra forma de fazer selects para criar filtros
* **Exemplo:**
```csharp
contexto.Entry(produto)
        .Collection(p => p.Compras)
        .Query()
        .Where(etc)
```