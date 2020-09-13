# Aula 02 - Sites responsivos

Observação: esse resumo foi elaborado no dia 21/05/2020.

### → Seletores
* `* { }` → seletor universal
    * Todos os elementos serão afetados pelas definições aqui contidas
    * Prioridade baixíssima

### :eight_spoked_asterisk: Boas práticas
* Deixar propriedades em ordem alfabética dentro dos seletores
* Fazer um reset de `margin` e `padding` "antes" de começar o site
```css
/* Soft reset: */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
* Declarar seletores e tags no CSS por ordem de existência no HTML
```css
/* 1º */
* { }

/* 2º */
body { }

/* 3º */
header { }
```
* Desenvolver pensando primeiro no mobile
    * Resolve problemas "mais rápido"

### → Propriedades
* `box-sizing` → define como a largura e altura de um elemento é calculado
    * :warning: A altura e largura incluem conteúdo, padding e borda
    * **Exemplos de valores:** `border-box`
* `position` → mexe com o eixo z da tela
    * "Empilha" coisas
    * :warning: Imune contra o `display: flex;`
    * **Exemplos de valores:** `fixed`
* `top` → só funciona quando tem um `position` declarado
    * Posiciona elemento no topo (valor 0, por exemplo)
    * **Exemplos de valores:** valores numéricos

### :warning: Centralizar verticalmente
* Uma das tarefas mais difíceis do CSS

### → HTML
* `div`
    * Agrupa sem alterar significado
    * Não tem significado semântico
    * Dá suporte à construção de layout
    * Extremamente genérica

### :eight_spoked_asterisk: `display: flex;`
* Só enxerga um nível abaixo
    * `header` → `flex`
        * `nav`
        * `div`
            * `h1` → não é afetado pelo flex
            * `h2` → não é afetado pelo flex

### :eight_spoked_asterisk: Alinhar no centro da tela
`display: flex;` :heavy_plus_sign: `justify-content: center;` :heavy_plus_sign: `align-itens: center;`

### :eight_spoked_asterisk: Para "debugar" CSS
`background-color: red;`

### :warning: `<a>`
* É uma tag **inline**
* Não quebra linha quando inserida
* Não consegue "receber" `padding`
* **Solução para aumentar área de clique de um botão:** `display: block;` :heavy_plus_sign: `padding: 10px 10px;`
    * `display: block` → "sobrescreve" valor padrão do inline

### → Atalhos VSCode
* `link:css` → gera tag para adicionar CSS à uma página
* `meta:vp` → gera tag para "adaptar" site para mobile
    * "Ajusta" largura/campo de visão

### :warning: ATENÇÃO!
* `vh` → altura
    * **`height: 100 vh;`**
* `vw` → largura
    * **`width: 100 vw;`**

### → Meta tag Viewport
```css
<meta name="viewport" etc>
```
* Habilita criar condições no CSS ("if")
* **Notação:** @
```css
@media(/*condição de tamanho*/) { }
```
* Entender o que precisa ser ajustado dentro dessa tag é o que torna um site responsivo
* **Exemplo de condição de tamanho:** `min-width: 400px`
    * Tamanho mínimo que a tela precisa ter para carregar os estilos

### → Tags `H` (h1, h2, h3, etc)
* Estilos padrão dos navegadores
* **CHROME:** user agent stylesheet

### :eight_spoked_asterisk: Unidade de Medida `em`
* Propriedade é **x vezes maior** que o tamanho declarado no body (ou padrão)
    * Unidade de medida relativa