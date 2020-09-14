# Aula 03 - Colunas e Linhas

Observação: esse resumo foi elaborado no dia 21/05/2020.

### :eight_spoked_asterisk: Bom recurso
* **Google Fonts**
    * Permite escolher fontes já "hospedadas", anexá-las via `<link>` e usá-las normalmente no CSS com `font-family`

### → Atributos
* **`alt` (tag `img`)**
    * Obrigatória
    * Proporciona acessibilidade para deficientes visuais

### :eight_spoked_asterisk: Atalho VSCode
* **`.[nomeclasse]`** → gera uma `div` com o atributo `class` declarado e preenchido
```html
<div class="nomeclasse"></div>
```

### → How to: grid
1. **Propriedade -** `display: grid;`
    * Próximas propriedades só funcionam após a declaração do grid
2. **Propriedade -** `gap: 1em;`
    * Espaçamento entre linhas/colunas
3. **Propriedade -** `text-align: center;`
    * Centraliza o grid
    * Pode ser aplicado na tag `figure`
4. **Propriedade -** `grid-template-columns: 180px;`
    * Define quantidade de colunas do grid
    * Opcional

### :eight_spoked_asterisk: Diferença entre flex e grid
* **flex:** CSS controla as colunas sozinho
* **grid:** mais específico ("preciso de x colunas")

### → Funções em CSS
* `repeat()` → serve para criar repetições
    * Como parâmetros, vai o número de repetições e o tamanho
    * **Exemplo:** criar duas colunas de 180px cada
    ```css
    grid-template-columns: repeat(2, 180px);
    ```
* `calc()` → faz cálculo entre unidades de medida diferentes automaticamente
    * **Exemplo:**
    ```css
    height: calc(100vh -48px -8em);
    ```

### :eight_spoked_asterisk: @media pode ser usado para melhorar experiência de grids
**Exemplos:**
* `@media(min-width: 560px) { }`
    * Melhor deixar com duas colunas somente
* `@media(min-width: 880px) { }`
    * Melhor ter três colunas e centralizar

### → Propriedades para imagens
* `object-fit` → corta a imagem, porém preservando seu aspecto e preenchendo o espaço previamente definido
    * **Exemplos de valores:** `cover`
* `object-position` → especifica como uma imagem ou vídeo deve ser posicionado em relação ao seu eixo x e y
    * **Exemplos de valores:** `valor-eixo-x valor-eixo-y`
* `border-radius` → arredonda as bordas
    * **Exemplos de valores:** valor em qualquer unidade de medida