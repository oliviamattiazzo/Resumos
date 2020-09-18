# Aula 02 - Organizando seus testes

Observação: esse resumo foi elaborado no dia 23/06/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Assert.Equal
* Método com sobrecarga para vários tipos diferentes

### → Questão: como saber que os testes estão prontos?
* Quantos testes são necessário para assegurar o funcionamento de um programa?

### :heavy_check_mark: Objetivos da aula
1. Quantos testes são o bastante?
2. Será que estou criando os testes certos? Quais cenários devo testar?
3. Como organizo meus testes? Que nome devo dar às classes e métodos de testes?

### :question: Como saber que há testes o suficiente? Que estão prontos?
* **Dica 1 -** procurar orientação de profissionais mais experientes
* **Dica 2-** usar o padrão de testes sob três sessões (AAA ou Given-When-Then)

### → Técnica de teste: classes de equivalência
* Observar valores de entrada e saída
* Divide os dados em várias partições para tornar os testes mais eficientes
* Possibilidade de redução de cenários de teste
    * Evitar testes "repetidos"

### → Extra: .DefaulfIfEmpty()
* É do `System.Linq()`
* Define um retorno quando a sequencia for vazia
* **Exemplo:**
    ```csharp
    Lances
        .DefaultIfEmpty(new Lance(null, 0))
        .LastOrDefault();
    ```

### → Notação `[Theory]`
* Pertence ao xUnit
* Depende da notação `[InlineData]`
    * Fornece os dados de entrada para a teoria
    * Em seu construtor, passamos os dados de entrada
* **Exemplo:**
```csharp
[Theory]
[InlineData(1200, new double[] { 800, 900, 1000, 1200 })]
[InlineData(1000, new double[] { 800, 900, 1000, 990 })]
[InlineData(800, new double[] { 800 })]
public void LeilaoComVariosLances(
                            double valorEsperado,
                            double[] ofertas
)
{
    /* 
        → Foreach para usar valores do array ofertas
        → valorEsperado vai para Assert
    */
}
```
* `[Theory]` indica a teoria
* Cada `[InlineData]` vai criar um teste diferente
* Os dados do `[InlineData]` vão ser passados para os parâmetros da função conforme a ordem

### → Fact vs Theory
* **Fact** → Não importa quais dados são passados e a expectativa segue a mesma
* **Theory** → Passa-se dados de entrada e a expectativa muda

### → Melhores práticas para nomenclatura de testes
* Por Microsoft
* O nome de um teste deve consistir de três partes
    1. O nome do método sendo testado
    2. O cenário
    3. O comportamento esperado para aquele cenário
* Também pode-se colocar o nome do método que está sendo testado como nome da classe
    * Métodos ficam com cenário e o comportamento esperado

### → Para saber mais
* Equivalence partitioning
* Boundary-value analysis
* [MemberData] do xUnit