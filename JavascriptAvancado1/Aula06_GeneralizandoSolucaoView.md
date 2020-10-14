# Aula 06 - Generalizando a solução da nossa View

Observação: esse resumo foi elaborado no dia 27/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:eight_spoked_asterisk: ES6 permite atribuir um valor padrão para parâmetros de funções
* **Exemplo:** `constructor(parametro = '') { }`

:eight_spoked_asterisk: Em Javascript, uma string sem conteúdo é avaliada como falso
* **Exemplo:** 
    ```javascript
    return model.texto ? 
            `<p class="alert alert-info">${model.texto}</p>` :
            `<p></p>`;
    ```
    * Se `model.texto` tem conteúdo, mostra a mensagem. Senão, mostra um parágrafo vazio.

### → Herança em Javascript
* `class NomeClasse extends OutraClasse { }`
    * `OutraClasse` → não esquecer de declará-la na `index.html`
    * :eight_spoked_asterisk: **Importante:** precisa ser declarada antes de todas as views herdeiras
* Usar método `super(parametro)` para enviar o parâmetro ao construtor da classe pai

### → Métodos "abstratos"
* Criar método na classe pai que lança uma exceção
    * Quando não for implementado o método nos herdeiros, o programador será "avisado"
    * **Exemplo:**
    ```javascript
    _template() {
        throw new Error('O método template deve ser implementado.');
    }
    ```

:eight_spoked_asterisk: Construtor da classe filha tem 2 parâmetros, e agora?
1. Cria o construtor na classe filha
2. Faz o `super()` do parâmetro necessário para a classe pai
* :warning: Precisa ser a primeira instrução!
* **Exemplo:**
    ```javascript
    constructor(nome, func) {
        super(nome);
        this._func = func;
    }
    ```
    * Caso contrário, teria erro porque estamos tentando acessar um `this` que ainda não foi inicializado

:eight_spoked_asterisk: Herança no Javascript → reutilização de código