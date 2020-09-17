# Aula 01 - Promovendo rápido feedback

Observação: esse resumo foi elaborado no dia 22/06/2020, se houve alguma atualização na aula do curso, esta não foi contemplada aqui.

### → Como saber se o código está funcionando?
* Pessoa e/ou equipe de teste podem mandar feedbacks
    * :warning: Demora
        * **Testes automatizados** → aumentam segurança e confiança no código

**:eight_spoked_asterisk: Negócio a ser usado como exemplo:** Sistema de Leilão

### → Teste
* **Definição:** fazer uma **avaliação**, uma verificação, uma checagem

### → Teste de software 
* Processo que acontece para **verificar se o software está atendendo os requisitos**

### → Automatizar o teste
* **Substituir o trabalho manual pelo trabalho da máquina**
    * :heavy_plus_sign: rápido
    * :heavy_minus_sign: pensar em cima

### → Objetivos da aula
1. Como garantir que meu **sistema está pronto**?
2. Como garantir que meu **sistema não tem problemas** ou defeitos?

### → Pattern Arrange Act Assert (AAA)
* Organizar o método de teste em **3 seções funcionais**
    1. **Arrange** - arranjar todas as pré-condições para o teste
    2. **Act** - agir no objeto ou método que está sendo testado
    3. **Assert** - verificar se os resultados esperados aconteceram

:warning: Testes feitos via projeto de console não tem o Assert automatizado (geralmente)

### → Teste unitário
* Testa **uma unidade de trabalho** específica
    * Não necessariamente um único método

### → Frameworks de teste
* Bibliotecas que auxiliam a não ter que ficar construindo testes em aplicações console
* **Três maiores concorrentes para .NET**
    * xUnit → vai ser o usado no curso
        * Própria Microsoft está usando o xUnit internamente
    * MSTest
    * NUnit

### → Notação para indicar método de teste
* Fact
```csharp
[Fact]
public void MetodoTeste()
{
}
```

### :eight_spoked_asterisk: Conteúdo extra
* Definições de teste
    * softwaretestingfundamentals.com/definition-of-test
* Pattern para teste automatizado AAA
    * wiki.cz.com/?ArrangeActAssert
* Pattern para teste automatizado GWT
    * martinfowler.com/bliki/GivenWhenThen