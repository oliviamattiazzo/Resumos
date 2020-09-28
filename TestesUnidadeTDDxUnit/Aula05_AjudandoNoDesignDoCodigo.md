# Aula 05 - Ajudando no design do código

Observação: esse resumo foi elaborado no dia 05/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:eight_spoked_asterisk: Novas implementações podem exigir uma alteração na interface de uma classe (ou seja, como ela interage com outras classes)
* **Design OO** → processo de planejar a interface de uma classe
    * TDD pode ajudar com o design

:eight_spoked_asterisk: **Definição:** a "interface do objeto" define como se pode interagir com ele
* O processo de elaborar a forma como os objetos interagem entre si é chamado *design*
* **Maneiras de se interagir com um objeto:** métodos, propriedades, construtor

:eight_spoked_asterisk: Testes automatizados simulam iteraçºoes que podem ser feitas com as classes de negócio
* Validam o design das interfaces das classes de negócio

:eight_spoked_asterisk: **Após teste funcionando,** avaliar uma possível refatoração de código
* Aprimoramento através de princípios como o **SOLID**
    * Objetivos → transformar o design em sistemas mais flexíveis, fáceis de manter e de entender
    * Princípio **S** fala sobre a  facilidade de um sistema em ser mantido
    * Cuidado com o alto acoplamento!
    
:eight_spoked_asterisk: Testes de regressão também ajudam quando há um redesign nas classes

### :back: SOLID
* **S**ingle responsibility principle
* **O**pen/Close principle
* **L**iskov substitution principle
* **I**nterface segregation principle
* **D**ependency inversion principle
