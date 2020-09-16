# Aula 05 - Efeitos visuais

Observação: esse resumo foi elaborado no dia 22/05/2020.

### :eight_spoked_asterisk: Atalhos VSCode
* `Lorem [enter]` → gera Lorem Ipsum
    * `Lorem*X` → para gerar **X** linhas de Lorem Ipsum

### → Propriedades
* `text-indent` → define o "recuo" de um parágrafo
* `clip-path` → corta a imagem em formatos variados
    * **Recurso:** bennettfeely.com/clippy
        * Tem várias formas pré-definidas
* `transform-style` → preserva as transformações 3D dos elementos filhos
    * **Exemplos de valores:** `preserve-3d`
* `perspective` → dá perspectiva à elementos 3D
    * Quanto maior o valor, mais longe do usuário

### :eight_spoked_asterisk: Boa prática
* Só trazer a propriedade quando ela é realmente necessária

### :eight_spoked_asterisk: Centralizar conteúdo de maneira "oldschool"
`margin-left: auto;` :heavy_plus_sign: `margin-right: auto;`

### :eight_spoked_asterisk: Classe funcional
* Classe que contém várias propriedades e é usada junto de outras classes no HTML
* **Exemplo:** .container
* **HTML:** `class="contato container"`

### :eight_spoked_asterisk: Recurso
* caniuse.com
    * Dá para verificar a usabilidade de uma propriedade (inclusive por navegador)