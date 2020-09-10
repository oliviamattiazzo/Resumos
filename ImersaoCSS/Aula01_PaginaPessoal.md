# Aula 01 - Página pessoal

Observação: esse resumo foi elaborado no dia 18/05/2020.

### → CSS
* `.menu` → **.** é um seletor de **classe**
    ```html
    <nav class="menu">
    ```
* `#menu` → **#** é um seletor de **id**
    ```html
    <nav id="menu">
    ```
* `a:hover` → **pseudoclasse** do CSS
    * Semelhante aos eventos da orientação a objeto
* `.menu li` → **seletor hierárquico**
    * Vai selecionar todos os elementos *li* dentro da tag com classe *menu*
    ```html
    <nav class="menu">
        <li></li>
        <li></li>
    </nav>
    ```
    * :warning: Tomar cuidado em **como montar a hierarquia**, pois pode causar lentidão (CSS demora para localizar o elemento)

### :warning: Seletor Id
* Não foi criado para CSS
* Existe uma **ordem de prioridade** de carregamento de seletores → id tem uma prioridade muito grande (a maior)
    * Sobrescreve qualquer outra coisa

### :eight_spoked_asterisk: Boa prática
* Deixar seletores próximos dentro do arquivo CSS
```css
.menu { }
.menu li { }

a { }
a:hover { }
```

### → Propriedades
* `text-decoration` → muda um texto, como tirar o underline de um link, pode ser usado em `hover`
    * **Exemplos de valores:** `none`, `underline`
* `list-style` → tira as bolinhas de uma lista (elemento `li`)
    * **Exemplos de valores:** `none`
* `display` → deixa elementos um ao lado do outro quando usado em um `ul`
    * **Exemplos de valores:** `flex`
* `justify-content` → deixa o conteúdo "justificado"; cria espaços entre colunas
    * :warning: Só funciona em conjunto com o `display: flex`
    * **Exemplos de valores:** `space-between`, `space-around`


### → Reaproveitamento de código em CSS
```css
.site-title,
.site-subtitle {
    /*propriedades*/
}
```
* Os dois seletores usarão as mesmas propriedades

### :eight_spoked_asterisk: Unidades de medida relativas
* Estão relacionadas a outras propriedades
* `vh` → relativo à 1% da altura do viewport
    * **Viewport** → o tamanho da janela do browser