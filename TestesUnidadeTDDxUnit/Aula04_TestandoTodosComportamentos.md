# Aula 04 - Testando todos os comportamentos

Observação: esse resumo foi elaborado no dia 01/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### :question: Como testar exceções de modo elegante e prático com xUnit?

### :eight_spoked_asterisk: Novo método da classe Assert
* `.Throws<>`
    * Dentro do `<>` vai o tipo da exceção esperada
    * `() =>` → passagem de método via delegates
    * Depois da `=>` → método a ser testado

```csharp
Assert.Throws<InvalidOperationException>(
    () => leilao.TerminaPregao()
);
```

:eight_spoked_asterisk: Para testar valores e propriedades que estão dentro da exceção: capturar a exceção em uma variável
```csharp
var excecaoObtida = Assert.Throws<>
```

### :eight_spoked_asterisk: Atalho VSCode
* **ctor** → cria um construtor