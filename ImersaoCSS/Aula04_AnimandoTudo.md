# Aula 04 - Animando tudo!

Observação: esse resumo foi elaborado no dia 22/05/2020.

### :eight_spoked_asterisk: Bom recurso
* **Font awesome**
    * Permite acessar e usar ícones no site
    * Adiciona o "kit" de ícones no site via tag `<script>`

### → Propriedades boas para animações
* `text-shadow` → coloca sombra em um texto
    * **Exemplos de valores:** `valor-eixo-x valor-eixo-y blur cor`
    * **Exemplo:**
    ```css
    text-shadow: 0px 0px 50px rgba(145, 141, 196, 0.5);
    ```

### :eight_spoked_asterisk: Para cores: rgba(x, y, z, a)
* **x** → red
* **y** → green
* **z** → blue
* **a** → transparência
    * Vai de 0 a 1

### → Propriedades de animação
* `transition` → inserida no seletor "original", adiciona "tempo" à animação
    * **Exemplo:** Se o destino for `a:hover`, colocar no `a`
    * Indicar quais propriedades do elemento vão ser alteradas
    ```css
    /*Exemplo 1*/
    transition: background-color, color, 2s;

    /*Exemplo 2*/
    transition: background, 2s, color, 2s;
    ```
    * **Exemplos de valores:** propriedades separadas por vírgula e tempo da animação em segundos
    * **Boa prática:** declarar sempre as propriedades
* `transform` → rotaciona, inclina ou escala um elemento
    * **Exemplos de valores:** uma **função**
        * `skew()` → graus como unidade de medida (deg)
        * `scale()` → valor da escala (Exemplo: **z** → dobra a foto)
        * `rotate()` → graus como unidade de medida (deg)
* `opacity` → propriedade mais adequada para fazer animação com transparência
    * **Exemplos de valores:** entre 0 e 1
        * 0 → transparente
        * 1 → opaco
* `animation` → vincula uma animação a um elemento `<div>`
    * **Exemplos de valores:** tipo movimento +/ou tempo +/ou nome da animação

### → Evento
* `:active` → para mobile
    * Quando o usuário toca no elemento

### → Criando uma animaçºao para usar na propriedade
* `@keyframes` → declaração da animação
    ```css
    @keyframes animacaoTitulo { }
    ```
    * Funciona por porcentagem da animação
        ```css
        0% { }
        100% { }
        ```
        **OU** por
        ```css
        from { }
        to { }
        ```
### :eight_spoked_asterisk: Linkar section no menu
```html
<a href="#id_da_secao"></a>
```