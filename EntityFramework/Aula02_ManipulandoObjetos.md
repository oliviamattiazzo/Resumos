# Aula 02 - Manipulando objetos

Observação: esse resumo foi elaborado no dia 18/01/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → .ToList()
* Equivalente ao **SELECT * FROM**
* **Exemplo →** Para retornar todos os itens de uma tabela de Produtos

```csharp
contexto.Produtos.ToList();
```

### → .Remove(item)
* Equivalente ao **DELETE FROM**
* Precisa do *.SaveChanges()* ao final do processo
* **Exemplo →** Para excluir cada um dos itens de uma tabela de Produtos

```csharp
foreach(var item in lstProdutos)
{
    contexto.Produtos.Remove(item);
}
contexto.SaveChanges();
```

### → .First()
* Equivalente ao **SELECT TOP 1**
* **Exemplo →** Selecionar o primeiro item de uma tabela de Produtos

```csharp
Produto primeiro = contexto.Produtos.First();
```

### → .Update(item)
* Equivalente ao **UPDATE... SET...**
* Precisa do *.SaveChanges()* ao final do processo
* **Exemplo →** Atualizar um dado de um registro de uma tabela de Produtos (através de uma propriedade do modelo)

```csharp
primeiro.Nome = "Novo nome";
contexto.Produtos.Update(primeiro);
contexto.SaveChanges();
```

### :eight_spoked_asterisk: Uma boa DAO
* Variável para contexto
```csharp
private LojaContext contexto;
```
* Construtor da classe com instanciamento do contexto
* Herdar classe IDisposable e implementar método Dispose para se desfazer do contexto
```csharp
contexto.Dispose();
```
* Quaisquer outros métodos relacionados à banco de dados