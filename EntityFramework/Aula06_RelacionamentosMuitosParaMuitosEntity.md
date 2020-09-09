# Aula 06 - Relacionamentos Um para Muitos no Entity

Observação: esse resumo foi elaborado no dia 09/02/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:warning: Não esquecer de colocar tabelas/classes no contexto antes de adicionar uma Migration!
```csharp
public DbSet<Promocao> Promocoes { get; set; }
```

:eight_spoked_asterisk: Entity não compreende corretamente o relacionamento N:N, representado no código por uma `IList<>`

Exemplo:

```csharp
classe Promocao {
    IList<Produtos>
}

//não vai se transformar em:

.AddColumn<int>(
    name: "PromocaoId",
    table: "Produtos"
);
```

* Como resolver?
→ **Resposta:** criando outra lista, na outra classe, que define o relacionamento
```csharp
classe Promocao
    IList<Produto>

classe Produto
    IList<Promocao>
```

* **Porém** só funciona no Entity Framework "normal"
    * O reconhecimento automático de tabelas de relacionamento não migrou para o Entity Framework Core e precisa ser feito na mão

    ```csharp
    public class PromocaoProduto {
        int ProdutoId
        Produto Produto
        int PromocaoId
        Promocao Promocao
    }

    classe Promocao ou Produto
        IList<PromocaoProduto>
    ```

:eight_spoked_asterisk: **Migrations requer que toda tabela tenha uma chave primária**, porém tabelas de `JOIN` não precisam de um campo específico para isso
* Chave primária composta!
```csharp
class PromocaoProduto → PK = ProdutoId + PromocaoId
```
* Para compor uma chave primária composta na criação da tabela via contexto, usar método `OnModelCreating()`
```csharp
protected override void OnModelCreating (ModelBuilder modelBuilder)
```
* Dentro do método, indicar a entidade e **usar o método .HasKey() para indicar os campos que compõe a chave**
```csharp
modelBuilder
    .Entity<PromocaoProduto>()
    .HasKey(pp => new { pp.PromocaoId,
                        pp.ProdutoId });
```

:warning: Não esquecer de, ao final, chamar o método da base para seguir processo
```csharp
base.OnModelCreating(modelBuilder);
```

:eight_spoked_asterisk: Para não deixar a classe da tabela de `JOIN` "descoberta" no código, **criar método dentro das classes** do relacionamento que servirão **para manipular o `JOIN`**
* Encapsulamento, bitch!
```csharp
promocao.IncluirProduto(p1);
```

:eight_spoked_asterisk: Quando deletamos uma parte do relacionamento, **o efeito será em cascata**, conformo configurado na Migration
* **Exemplo:** Quando apago `Promocao`
    * Produtos criados seguem na tabela `Produtos`
    * `PromocaoProdutos` é apagada