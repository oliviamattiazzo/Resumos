# Aula 04 - Lidar com data é trabalhoso? Chame um ajudante!

Observação: esse resumo foi elaborado no dia 16/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Helper
* Isolar responsabilidade de manipulação de dados
    * Métodos de conversão (DataParaTexto e TextoParaData)
    * :eight_spoked_asterisk: Lembrar de adicionar o helper na página HTML

:eight_spoked_asterisk: Várias instâncias podem impactar no uso da memória

### → Métodos estáticos
* Não precisam que as classes sejam instanciadas para usar os métodos
* Colocar `static` antes do nome do método
    * **Exemplo:** `static dataParaTexto() { }`
* Classes estáticas não podem ter constructor
    * Se criar, usar para apontar erro → `throw new Error('mensagem');`

### → Template string
* Interpolação de strings com variáveis
* Usar crase e ${ }
* **Exemplo:**
    ```javascript
        console.log(`A idade de ${nome} é ${idade}.`);
    ```

:eight_spoked_asterisk: **Testar padrão de uma string com regex**
* /regex/.test(variável)
* **Exemplo:** `/\d{4}-\d{2}-\d{2}/.test(texto)`
    * Testa se está no formato YYYY-MM-dd

### → List model
* Criar uma lista
* Criar array dentro do constructor()
    * Privado
    ```javascript
    constructor() {
        this._negociacoes = [];
    }
    ```
* Criar métodos de manipulação
    * `adiciona(negociacao) { }`
    * `get negociacoes() { }`
* Criar lista como propriedade
    * `this._lstNegociacoes = new ListaNegociacoes();`

:eight_spoked_asterisk: **Métodos privados** seguem a convenção de começar seus nomes com '_' (underline)

:eight_spoked_asterisk: Lembrar de adicionar o modelo da lista no index.html

### → Programação defensiva com listas
* No get da list model, retornar uma "cópia" do array privado
    ```javascript
    get negociacoes() {
        return [].concat(this._negociacoes);
    }
    ```
* "Blinda" de operações "erradas"

:eight_spoked_asterisk: **Regex para data:** /^\d{4}-\d{2}-\d{2}$/
* **^ →** começando com
* **$ →** terminando com