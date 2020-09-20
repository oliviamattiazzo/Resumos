# Aula 03 - Não deixe o sistema regredir

Observação: esse resumo foi elaborado no dia 28/06/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

:eight_spoked_asterisk: Testes automatizados dão um **feedback muito rápdio se o sistema regrediu** com uma nova implementação
* **Testes de regressão** → evitam a regressão do sistema

:eight_spoked_asterisk: Às vezes, **manutenção nos cenários de teste são necessárias**
* Testes também precisam ser removidos pois não fazem mais sentido em um contexto

:eight_spoked_asterisk: **Código de qualidade nos testes também é importante!**

### :question: Como evitar que a implementação de novas funcionalidades quebre o sistema?
* Testes de regressão **aumentam confiança no código**

### :question: Como garantimos testes para cada nova funcionalidade?
* **Comum:** tester ou equipe de QA
    * Testa os incrementos de software
    * Dev livre para programar com respaldo
    * **Mas...** → dependência de outros para testes torna o trabalho mais demorado e menos dinâmico
* **Testes automatizados** → feedback imediato
    * Otimiza tempo de trabalho
    * Total controle sobre o programa

### :eight_spoked_asterisk: Alterar orientação do fluxo de trabalho
* Criar primeiro o teste, depois escrever o código do negócio
    * Criar cenário inicial na classe de teste, com falha em um primeiro momento
    * Escrever o código da funcionalidade para que o teste passe
    * **:arrow_right: TDD** 
        * **T**est **D**riven **D**evelopment
        * Muito usado em times ágeis
        * Parece contraintuitivo
        * Carece disciplina

### :warning: Testar métodos privados?
* Na maioria dos casos, não é necessário
* Em algum ponto, vai haver um método público que está sendo testado que chama o método privado
* O importante é o resultado final do método público
* Métodos privados são um detalhe de implementação

### → Ciclo TDD
![Ciclo do TDD](https://github.com/oliviamattiazzo/Resumos/blob/master/TestesUnidadeTDDxUnit/CicloTdd.png)