# Aula 02 - Especificando uma Negociação

Observação: esse resumo foi elaborado no dia 14/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → O que é um Modelo?
* É uma **abstração do mundo real**
* Cria-se um Modelo para as coisas e este deve conseguir programaticamente fazer tudo que as coisas na vida real são capazes de fazer
* Recurso do paradigma OO → **criação de classes**
    * :eight_spoked_asterisk: Antes do ES6, já era possível criar classes em Javascript, porém a sintaxe era muito complexa
* **Classe →** especificação da abstração

### → Convenção de Nomenclaturas
* **Classes →** nome começa com letra maiúscula
    * `Nomenclatura.js`
    * :eight_spoked_asterisk: Pouco comum para JS, mas deixa claro que é uma classe
* Nome da classe igual ao nome do arquivo
    * `class Negociacao { }`

### → Classes Javascript
* **Atributos →** função `constructor()`
    ```javascript
    constructor() {
        this.data = new Date();
        this.qtde = 1;
        this.valor = 0.0;
    }
    ```
:eight_spoked_asterisk: `new Date()` → preenche com a data atual por padrão

* **Instanciar →** `var c1 = new Classe();`
    * `new` → responsável pela inicialização do `this` de cada objeto
    * :eight_spoked_asterisk: **this →** variável implícita
        * Apontará para a instância que está executando a operação naquele momento
    * :eight_spoked_asterisk: Função `constructor()` aceita parâmetros
        * :warning: Atenção sempre com a ordem dos parâmetros

* **Criar método na classe →** `nomeDoMetodo() { }`
    ```javascript
    obtemVolume() {
        return this.qtde * this.valor;
    }
    ```
:eight_spoked_asterisk: Programação OO tem uma forte conexão entre o dado e o comportamento.

### → Javascript não permite uso de modificadores de acesso
* Pelo menos até a data do curso
* Utilizar **convenção de nomes** → o que não pode ser modificado, começa com underline
    * `this._qtde` para atributos privados
* Criar métodos acessadores para printar campos privados
    * Nomenclatura = `get Campo()`

### → Sintaxe get
```javascript
get Campo() {
    return this._campo;
}
```
* Mesmo sendo um método, acessamo-os como uma propriedade
    * `instancia.campo`
    * `console.log(n1.data);`
* Propriedade getter → somente leitura

### → Congelar objetos
* `Object.freeze(var);` | `Object.freeze(n1);`
* `.isFrozen()` → verifica se o objeto está congelado ou não
* `Object.freeze(this);` → deixa a classe impossível de ser alterada
    * Equivalente ao `private set;`
    * **Observação:** dentro do construtor

:eight_spoked_asterisk: `Object.freeze()` não torna as instâncias completamente imutáveis
* `n1.data.setDate(15);`
* `Object.freeze` fica na superfície (shallow)
    * É necessário fazer um *deep freeze* **OU** aplicar uma **programação defensiva**

### → Programação defensiva
* Quando chamar o getter de uma propriedade, retornar uma nova instância com o mesmo valor
```javascript
get data() {
    return new Date(this._data.getTime());
}
```
* Quando for setar uma propriedade (no construtor, por exemplo), criar uma nova instância com o mesmo valor
```javascript
this._data = new Date(data.getTime());
```

### → var e let
* Em Javascript não existe o escopo de bloco
* **var** → "vaza" do bloco; escopo global
* **let** → faz as variáveis terem escopo de bloco

### :eight_spoked_asterisk: Pascal case
* Primeira letra maiúscula
* **Exemplo:** nomes de classes

### :eight_spoked_asterisk: Propriedade ou atributo
* Tanto faz
* **Propriedade →** mundo JS
* **Atributo →** mundo OO

### :eight_spoked_asterisk: **TypeScript** 
* Permite definir atributos privados (tem modificador `private`)
* Superset do ES2015+ (adição de novos recursos)

### :eight_spoked_asterisk: Date()
* É uma função construtora
* Sintaxe do ES6 são açúcares sintáticos do ES5

### :eight_spoked_asterisk: Javascript é uma linguagem multiparadigma
* Procedural
* Funcional
* OO 