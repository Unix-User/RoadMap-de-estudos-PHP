# Herança de Objetos

Herança é um conceito de programação estabelecido, e o PHP faz use deste em seu modelo de objetos. Este princípio afeta a forma com que classes e objetos se relacionam com outras.
Por exemplo, ao estender uma classe, a subclasse herda todos os métodos públicos e protegidos, propriedades e constantes da classe pai. A não que uma classe sobrescreva estes métodos, eles manterão sua funcionalidade original.
Isto é útil para definir uma funcionalidade abstrata, e permitir a implementação de uma funcionalidade adicional em objetos similares sem a necessidade de reimplementar todas as funcionalidades compartilhadas.
Os métodos privados de uma classe pai não são acessíveis a uma classe filha. Como resultado, as classes filhas podem reimplementar um método privado sem levar em conta as regras normais de herança. Antes do PHP 8.0.0, entretanto, as restrições final e static eram aplicadas aos métodos privados. Desde o PHP 8.0.0, a única restrição de método privado que é aplicada é private final para construtores, já que essa é uma maneira comum de "desabilitar" o construtor ao usar métodos de fábricação estáticos.
A visibilidade de métodos, propriedades e constantes pode ser relaxada, por exemplo, um método com `protected` pode ser marcado como `public`, mas não pode ser restrito, por exemplo, marcar uma propriedade que tenha `public` como `private`.

Nota:
A não ser que o autoload seja usado, as classes devem ser definidas antes de utilizadas. Se uma classe estende outra, a classe pai deve ser declarada antes da estrutura da classe filha. Esta regra se aplica a classes que herdam outras classes e interfaces.

## Exemplo
```
<?php

class Foo
{
    public function printItem($string)
    {
        echo 'Foo: ' . $string . PHP_EOL;
    }

    public function printPHP()
    {
        echo 'PHP is great.' . PHP_EOL;
    }
}

class Bar extends Foo
{
    public function printItem($string)
    {
        echo 'Bar: ' . $string . PHP_EOL;
    }
}

$foo = new Foo();
$bar = new Bar();
$foo->printItem('baz'); // Output: 'Foo: baz'
$foo->printPHP();       // Output: 'PHP is great'
$bar->printItem('baz'); // Output: 'Bar: baz'
$bar->printPHP();       // Output: 'PHP is great'

?>
```
# Compatibilidade de Tipo de Retorno com Classes Internas

Antes do PHP 8.1, a maioria das classes ou métodos internos não declaravam seus tipos de retorno, e qualquer tipo de retorno era permitido ao estendê-los.
A partir do PHP 8.1.0, a maioria dos métodos internos começaram a declarar seu tipo de retorno de forma "experimental", nesse caso o tipo de retorno dos métodos deve ser compatível com o pai sendo estendido, do contrário, uma notícia de depreciação é emitida. Note que a ausência de uma declaração de retorno explícita também é considerada uma incompatibilidade de assinatura e, portanto, resulta no aviso de depreciação.
Se o tipo de retorno não puder ser declarado para um método que sobrepõe devido à preocupações com compatibilidade entre versões PHP, um atributo #[ReturnTypeWillChange] pode ser adicionado para silenciar a notícia de depreciação.

## Exemplo 


```
<?php
// O método que sobrepõe não declara nenhum tipo de retorno
class MeuDateTime extends DateTime
{
    public function modify(string $modifier) { return false; }
}
// "Deprecated: Return type of MeuDateTime::modify(string $modifier) should either be compatible with DateTime::modify(string $modifier): DateTime|false, or the #[\ReturnTypeWillChange] attribute should be used to temporarily suppress the notice" a partir do PHP 8.1.0
?>
Exemplo #3 O método que sobrepõe declara um tipo de retorno errado

<?php
class MeuDateTime extends DateTime
{
    public function modify(string $modifier): ?DateTime { return null; }
}

// "Deprecated: Return type of MeuDateTime::modify(string $modifier): ?DateTime should either be compatible with DateTime::modify(string $modifier): DateTime|false, or the #[\ReturnTypeWillChange] attribute should be used to temporarily suppress the notice" a partir do PHP 8.1.0
?>
Exemplo #4 O método que sobrepõe declara um tipo de retorno errado sem uma notícia de depreciação

<?php
class MeuDateTime extends DateTime
{
    /**
     * @return DateTime|false
     */
    #[ReturnTypeWillChange]
    public function modify(string $modifier) { return false; }
}

// Nenhuma notícia é acionada
?>
```
> texto copiado integralmente de <a href="https://www.php.net/manual/pt_BR/language.oop5.inheritance.php">https://www.php.net/manual/pt_BR/language.oop5.inheritance.php</a>

Anterior [Parte 2 - Interfaces](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/05-Interfaces.md)
Próximo [Implementação](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/07-Implementation.md)
