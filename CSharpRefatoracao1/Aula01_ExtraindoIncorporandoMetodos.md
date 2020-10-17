# Aula 01 - Extraindo e incorporando métodos

Observação: esse resumo foi elaborado no dia 15/08/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Introdução
* **Código limpo**
    * Sem duplicação
    * Mais clareza
    * Menos classes
    * Mais enxuto
    * Fácil de manter
    * Passa em todos os testes
* **Débito técnico** → falta de tempo (ou chefia) para melhorar ou refatorar o código
* **Refatoração** 
    * Melhorar qualidade do código
    * Facilitar entendimento da equipe
    * Melhorar comunicação interna e trabalho da equipe

### → Dois tipos de  técnicas de refatoração
#### 1. Técnicas de composição
* Extrair método
* Incorporar método
* Extrair variável
* Incorporar variável temporária
* Substituir variável por consulta
* Quebrar variável
* Remover atribuições a parâmetros
* Substituir método por método objeto
* Substituir algoritmo

#### 2. Mover itens entre objetos
* Mover método
* Mover campo
* Extrair classe
* Incorporar classe
* Ocultar delegado
* Remover intermediário
* Introduzir método estrangeiro
* Introduzir extensão local

### → Extrair método
* **Métodos grandes →** rolagem do código dificulta a leitura
* **Comentários →** ajudam a entender o código **mas** podem se tornar desatualizados
    * Se desatualizados, podem enganar o desenvolvedor
* **Extrair método →** transforma trechos de código em métodos independentes
    * Diminui tamanho do método original
    * Facilita leitura
    * Pode eliminar comentários obsoletos
    * Pode ser feita via `Ctrl + .` no Visual Studio
    * **Quando refatorar?**
        * Código duplicado
        * Método muito grande
        * Comentários 
        * Cadeias de mensagens
    * **Quando não refatorar?**
        * Corpo do método vai ficar tão óbvio quanto nome

### :eight_spoked_asterisk: Código limpo - motivos pelos quais refatoramos
* Classes e métodos "extras" podem confundir a leitura
* Código duplicado exponencia quantidade de alterações → maior probabilidade de erro
* Um bom programa não só executa corretamente, mas também expressa bem o que está executando
* Quanto mais difícil a leitura de um código, mais tempo para diagnosticar bugs e falhas

### → Incorporar método
* Inverso do extrair método
* Corpo do método é tão evidente quanto o seu nome
* **Exemplo:**
    ```csharp
    bool TemMaisDeCincoEntregas() {
        return qtdeEntregas > 5;
        //incorporar expressão direto no método
    }
    ```
* **Quando não refatorar →** quando o corpo do método não é auto-explicativo

### :eight_spoked_asterisk: Code smells
* "Mal-cheiro" no código
* Indício de que algo está errado e precisa ser corrigido
* **Código duplicado →** não se repita (DRY - don't repeat yourself)
    * Extrair método pode ajudar
* **Método longo →** viola SRP (Single Responsibility Principle)
    * Difíceis de ler
    * **Métodos curtos →** mais fáceis de ler e comparar
    * Extrair método pode ajudar
* **Comentários →** não explicar direito
    * Desatualizados
    * Enganar desenvolvedor
    * Inibir refatoração
    * Extrair método pode ajudar

:eight_spoked_asterisk: Testes de unidade do código garantem que a refatoração não "quebre" as funcionalidades do sistema

:eight_spoked_asterisk: Refatoração não é correção de bugs nem criação de novas funcionalidades