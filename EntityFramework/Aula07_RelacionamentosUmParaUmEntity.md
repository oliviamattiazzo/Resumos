# Aula 07 - Relacionamentos Um Para Um no Entity

Observação: esse resumo foi elaborado no dia 07/05/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

* **Exemplo:**
    * `Cliente` - `Endereço` → relacionamento 1:1
        ```csharp
        class Cliente 
        {
            public Endereco EnderecoDeEntrega { get;set; }
        }

        class LojaContext
        {
            public DbSet<Cliente> Clientes { get; set; }
        } 
        ```

        → Console NuGet
        ```console
        Add-Migration Cliente
        ```
        :no_entry: Erro! → Classe Endereco vai ser mapeada pelo Entity porque está relacionada à classe Cliente

:eight_spoked_asterisk: Quando definimos uma entidade no contexto, o Entity navega por suas propriedades
* Caso o **tipo da propriedade seja outra classe, esta também passa a ser controlada pelo Entity**.

:eight_spoked_asterisk: Dependendo da lógica de negócio, não se mapeia algumas classes no contexto
* `Endereco` será manipulado somente por meio da classe `Cliente`

:eight_spoked_asterisk: Existem cenários de relacionamentos 1:1 onde a tabela dependente assume o Id da tabela principal
* **Exemplo:** EnderecoId é, na verdade, ClienteId
* Ajusta-se isso no método `OnModelCreating()`
```csharp
modelBuilder
    .Entity<Endereco>()
    .Property<int>("ClienteId");

modelBuilder
    .Entity<Endereco>()
    .HasKey("ClienteId");
```

:eight_spoked_asterisk: **Shadow Properties** são propriedades que não existem na classe que representa sua entidade, mas existem na tabela

:eight_spoked_asterisk: Quando precisa-se alterar o nome de uma tabela sem ser pela criação de um `DbSet`, usar o `OnModelCreating()`
* **Exemplo:**
```csharp
modelBuilder
    .Entity<Endereco>()
    .ToTable("Enderecos");
```