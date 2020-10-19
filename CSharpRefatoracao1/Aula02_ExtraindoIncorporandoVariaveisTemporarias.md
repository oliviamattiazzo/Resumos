# Aula 02 - Extraindo e incorporando variáveis temporárias

Observação: esse resumo foi elaborado no dia 16/08/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Extrair variável
* Extrair duplicações para uma variável (chamadas de métodos, por exemplo) **ou** quebrar uma expressão complexa em variáveis mais explicativas
* Opção via Visual Studio: :bulb: > Introduce local for `nome_metodo_selecionado` **OU** > Introduce local for all occurrences of `nome_metodo_selecionado`
* **Quando refatorar:** expressão complexa pode ser quebrada em partes mais simples **porém** haverá mais variáveis espalhadas pelo código

### → Incorporar variável temporária
* Inverso de Extrair Variável
* Visual Studio: :bulb: > Inline temporary variable
* Variável temporária que recebe valor só uma vez, de uma expressão simples
* **Quando refatorar:** expressão da variável é tão óbvia quanto seu nome
* **Quando não refatorar:** expressão da variável não é auto-explicativa
* **Exemplo:**
    ```csharp
    // Antes:
    decimal valorProdutos = pedido.ValorProdutos();
    return valorProdutos > 1000;

    // Depois:
    return pedido.ValorProdutos() > 1000;
    ```

### → Substituir variável por consulta
* Armazenamento do resultado de uma expressão em uma variável temporária
* **Exemplo:**
    ```csharp
    public CEP(string cepAsString) 
    {
        // Antes:
        string unformattedCep = cepAsString.Replace("-", "");

        // Depois:
        string unformattedCep = UnformatCep(cepAsString);
    }

    private static string UnformatCep(string cep) 
    {
        return cep.Replace("-", "");
    }
    ```
* Maior reaproveitamento de código
* Métodos como esses (`UnformatCep`) podem ser chamados de *Consulta* ou *Query*
* :eight_spoked_asterisk: Quando substituímos uma variável por um método de consulta, eliminamos duplicações indesejadas e permitimos que essa expressão possa ser avaliada a qualquer momento