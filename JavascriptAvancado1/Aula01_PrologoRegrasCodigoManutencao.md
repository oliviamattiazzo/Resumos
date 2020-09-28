# Aula 01 - Prólogo: regras, código e manutenção

Observação: esse resumo foi elaborado no dia 14/07/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Visão geral
* Curso **avançado**
* ECMAScript 2015 (**ES6**)
* Código organizado no **modelo MVC**
* Aplicação de **padrões de projeto**
* **Programação assíncrona** com promises
* **Renderização de templates**
* **Proxies**

### → Projeto
* Pastas **client** e **server**
    * **Client** → será carregada pelo servidor
    * **Server** → servidor Node.js

### → Infraestrutura
* Google Chrome versão 50 ou superior
    * **Importante!**
    * Muitos recursos do ES6
* Node.js v4.0

:eight_spoked_asterisk: **Como saber se determinada funcionalidade do ES6 é suportada por cada navegador?**
* [ECMAScript 6 compatibility table](https://kangax.github.io/compat-table/es6/)
* Nenhum recurso deste curso é experimental
    * Já fazem parte do ES6

### → Aquecendo e relembrando
* Atalhos do VSCode
    * Tag de importação de script
        * `script[src=js/index.js]`
        * Se torna `<script src="js/index.js"></script>`
    * `.querySelector`
        * Busca elemento do DOM através do seletor CSS
    * `.addEventListener`
        * Registra uma única espera de evento em um único alvo

### → DOM
* **Document Object Model**
* Representa o HTML através de elementos e objetos
*  "API" que podemos acessar com o Javascript

### → Problemas do código atual
* Não evidencia o negócio
* Mistura o negócio com a apresentação dos dados
    * **Aplicação do MVC**
        * Classes para os modelos e classes para as views
        * Ações serão interceptadas por uma **Controller**
            * Altera os dados (Model)
            * Atualiza a View
        * **Regras de negócio não ficam espalhadas**, ficam no Model
        * Paradigma da **Orientação à Objetos**
    
### → Extra: o que é ECMAScript?
* Javascript - 1995 - Brendan Eich
* Para que **a linguagem evoluísse obedecendo a determinados padrões e normativas, os criadores do Javascript se associaram ao ECMA** (European Computer Manufactures Association) em 1996
* *Javascript* já havia sido patenteado pela Sun (Oracle)
* Linguagem se tornou a ECMAScript
* **Hoje:** Javascript é o nome que ficou popular na comunidade e *ECMAScript é usado para referenciar a versão da linguagem*
    * **ECMA-262** que tem os padrões e normativas do Javascript
        * Participação de gigantes da tecnologia no grupo (Microsoft, Google)
    * **Atualmente:** ECMAScript 7 (2017)