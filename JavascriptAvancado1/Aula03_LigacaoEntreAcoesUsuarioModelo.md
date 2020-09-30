# Aula 03 - A ligação entre as ações do usuário e o modelo

Observação: esse resumo foi elaborado no dia 15/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Controller
* Convenção de nome: **Pascal case**
    * `NegociacaoController.js`
* Criar métodos com evento como argumento → `nomeMetodo(event) { }`
    * `adiciona(event) { }`
* Inserir controller na `index.html` com a tag `<script>`
    * ```html 
        <script src="js/app/controllers/NegociacaoController.js">
        </script>
    ```
* Instanciar o controller em uma tag `<script>`
    * ```html
        <script>
            let negCont = new NegociacaoController();
        </script>
    ```
* "Chamar" o método da controller no elemento HTML
    * Inspirado no AngularJS
        * Menos código no Javascript
    * ```html
        <form class="form" onsubmit="negCont.adiciona(event)">
    ```

### → First Class Functions
* Quando funções são tratas como qualquer outra variável
* **Exemplo:** imitar o jQuery
```javascript
let $ = document.querySelector.bind(document);
```
* **Chamada da função:**
```javascript
let var = $('#cmp');
```
* `.bind(document)` → Mantém a associação do querySelector com o document (caso contrário, há perda de contexto)

### → Evitar percorrer o DOM
* Melhorar performance
* "Cachear" a informação no `constructor()` do controller com criação de propriedades
```javascript
constructor() {
    this.inputData = $('#data');
    this.inputQtde = $('#qtde');
}
```
* Quando o controller for instanciado pela primeira vez, ele já busca os elementos do DOM e guarda nas propriedades
    * Depois é só ir acessando os valores

### → Descobrir o tipo de algo
* `typeof()`
```javascript
typeof(this._inputData.value)
// Resultado: string
```

### → Criar uma nova data a partir de string
* `new Date(campo.value.split('-'));`
    * `new Date()` → aceita array (strings ou número)
    * **Formato:** ['ano', 'mes', 'dia']
* `<input type="date" ...>`
    * **Formato:** YYYY-MM-dd
    * `.split('-')` funciona

:eight_spoked_asterisk: new Date()
* Também aceita string (formato: 'ano, mes, dia'), porém dados precisam ser separados por vírgula
    * `.replace(/-/g,',')`
        * `/-/g` → regex
        * `','` → troca todos os hífens por vírgula
* Aceita números → formato: `new Date(ano, mes, dia)`
    * `mes` → vai de zero a 11

### → Spread Operator
* `...this._campo.value.split('-')`
    * `...` → indica que o array será desmembrado e cada elemento ficará na ordem correta

### → Função .map()
* Chama a função recebida para cada elemento do array original
* **"Parâmetros"**
    * item
    * indice
* **Exemplo:**
    ```javascript
    _campo.value
          .split('-')
          .map(function (item, indice)) {
              return item + 10;
          }
    ```

### → Arrow Function
* Deixa o código menos verboso
* **Símbolo:** `=>`
* **Exemplo:**
    ```javascript
    .map((item, indice) => item + 10)
    ```
    * Elimina a necessidade do return e do ponto-e-vírgula

:eight_spoked_asterisk: **Controller** → recebe as ações do usuário e sabe interagir com o modelo
* Ponte entre View e Model

:eight_spoked_asterisk: `.addEventListener` nos obriga a manipular o DOM toda vez que associamos um evento ao elemento

:eight_spoked_asterisk: Guardar referências em "cache" é muito importante!
* Não sobrecarregue o DOM!
* Código otimizado e legível é amor

:eight_spoked_asterisk: **Métodos para arrays em JS**
* `.reverse()` → inverte a ordem de um array
* `.join('/')` → une os elementos do array em uma string, com uma barra separando-os

:eight_spoked_asterisk: `array1.push(...array2);`
* Vai adicionar os itens do array2 ao final do array1

:eight_spoked_asterisk: Spread operator pode ser usado na passagem de parâmetros
```javascript
let numeros = [10, 30];
somaDoisNumeros(...numeros);
```

:eight_spoked_asterisk: Quando a arrow function possui apenas um parâmetro, podemos remover os parênteses
```javascript
.map(prova => prova.aluno.nome)
```