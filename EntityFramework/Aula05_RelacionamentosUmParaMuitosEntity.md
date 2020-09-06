# Aula 05 - Relacionamentos Um para Muitos no Entity

Observação: esse resumo foi elaborado no dia 02/02/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:warning: Para remover uma Migration, existe o comando **Remove-Migration**
* Executar no console do NuGet

### → Modelo Relacional do BD não guarda referências de objetos
* Logo, quando há esse tipo de estrutura na classe, o Entity interpreta como `[classe] Id` na Migration
* Exemplo:
```csharp
classe Compra
prop Id (int)
prop Quantidade (int)
prop Produto (object)
prop Preco (double)
```
```csharp
//Método Up (Migration)
Id (int)
Quantidade (int)
ProdutoId (int)
Preco (double)
```

:warning: **Verificar métodos de Up e Down antes de executá-los**
* Condição de nulabilidade da coluna pode não estar adequada

:eight_spoked_asterisk: Para forçar com que campo que corresponderá a uma FK não possa ser nulo, **explicitar o nome do campo e um tipo de variável não nulável**
```csharp
//int não é nulo nunca
public int ProdutoInt { get; set; }
```

:eight_spoked_asterisk: Caso eu precise gravar um objeto que tem referência a outro objeto que ainda não foi gravado no BD, o Entity faz sozinho o processo de gravar ambos os objetos
```csharp
// 1. Grava pao e recupera o Id
// 2. Grava compra com o Id recuperado

Produto pao = new Produto();
compra.Produto = pao;
contexto.Compras.Add(compra);
contexto.SaveChanges();
```

