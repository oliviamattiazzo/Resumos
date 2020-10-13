# Aula 05 - Temos o modelo, mas e a View?

Observação: esse resumo foi elaborado no dia 17/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:eight_spoked_asterisk: **Template string** pode ser usado com HTML para facilitar a identação

### → View
* Precisa ser adicionada ao HTML
* Precisa ser uma propriedade no controller
* Cria-se uma `<div>` no HTML com o nome da view que conterá o resultado da renderização → `<div id="negociacaoView"></div>`
* Método `update()` → renderiza o template no elemento do DOM previamente definido
    * Função `innerHTML` → transforma texto em DOM
    * Pode ser passado por parâmetro para o construtor
        * Definição na controller

### → Template dinâmico com .map()
* Função `template()` recebendo a list model como parâmetro
* Tabela já "montada" com template string
* Dentro de `<tbody>`, fazer o `.map()` da list model montando as linhas da tabela
```javascript
<tbody>
    ${model.negociacoes.map(n => {
        return `
            <tr>
                <td>${n.campo1}</td>
                <td>${n.campo2}</td>
            </tr>`;
    })};
</tbody>
```

:eight_spoked_asterisk: Dentro do `${ }` da template string não se pode escrever blocos de código com instruções
* **Mas** pode-se adicionar uma função → **IIFE** ou **função imediata**
    * **IIFE** → **I**mmediately-**I**nvoked **F**unction **E**xpression
    * Colocar um bloco de código na expressão, sendo executado imediatamente
    * `(function() {})()`

### → .reduce()
* **Definição:** executa uma função reducer fornecida para cada elemento do array, resultando em um único valor de retorno
    * **Parâmetro 1:** function() ou arrow function
    * **Parâmetro 2:** valor inicial do primeiro argumento da function
* **Exemplo:**
    ```javascript
    array.reduce(function(total, n) {
        return total + n;
    }, 0.0);
    ```
    * `total` → retorno/acumulador
    * `n` → elemento "da vez"
* **Exemplo com arrow function:**
    ```javascript
    array.reduce((total, n) => total + n, 0.0);
    ```

:eight_spoked_asterisk: Vale a pena passar o segundo parâmetro da função reduce() porque, caso o array for vazio, a exceção *Reduce of empty array with no initial value* não será lançada

:eight_spoked_asterisk: Views declaradas no lado do JS se assemelham mais ao React (framework)