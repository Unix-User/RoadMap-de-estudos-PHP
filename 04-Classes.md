
# Classes no PHP

Uma classe é um template para objetos, e um objeto é uma instancia de uma classe.

## Programação orientada a objeto - OOP

Vamos assumir que temos uma classe chamada fruta, uma fruta tem propriedades como nome, cor, peso, etc. Pdemos definir variaveis como $name, $color e $weight para armazenar os valores dessas propriedades.

Quando os objetos individuais (maça, banana, etc.) são criados, eles herdam as propriedades e caracteristicas da classe, mas cada objeto tem valores diferentes para suas propriedades.

## Definindo uma classe

Uma classe é definida pelo uso da palavra chave `class`, seguida pelo nome da classe e um par de cochetes ({}). Todas as propriedades e metodos vão dentro dos cochetes.

```
<?php
class Fruit {
  // codigo vai aqui
}
?>
```
Abaixo declaramos uma classe chamada Fruit consistindo de duas propriedades ($name e $color) e dois metodos set_name() e get_name() para setar e pegar os dados da propriedade $name;

```
<?php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}
?>
```
Em uma classe, variaveis são chamadas de propriedades e funções são chamadas de metodos.

## Definindo objetos

Classes são nada sem objetos. Podemos criar multiplos objetos de uma classe. Cada Objeto tem todas as propriedades e metodos definidos na classe, mas eles tem diferentes valores em suas propriedades.

```
<?php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}

$apple = new Fruit();
$banana = new Fruit();
$apple->set_name('Apple');
$banana->set_name('Banana');

echo $apple->get_name();
echo "<br>";
echo $banana->get_name();
?>
```
No exemplo abaixo, adicionamos mais dois metodos para a classe Fruit, para setar e pegar a propriedade $color

```
<?php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
  function set_color($color) {
    $this->color = $color;
  }
  function get_color() {
    return $this->color;
  }
}

$apple = new Fruit();
$apple->set_name('Apple');
$apple->set_color('Red');
echo "Name: " . $apple->get_name();
echo "<br>";
echo "Color: " . $apple->get_color();
?>
```

## A palavra chave $this

A palavra chave `$this` se refere ao conjunto do objeto, e somente é disponivel atraves de metodos. Observe o seguinte exemplo
```
<?php
class Fruit {
  public $name;
}
$apple = new Fruit();
?>
```
Podemos mudar o valor da propriedade $name de 2 maneiras:

1 - Dentro da classe (adicionando um metodo set_name() e usando $this)

```
<?php
class Fruit {
  public $name;
  function set_name($name) {
    $this->name = $name;
  }
}
$apple = new Fruit();
$apple->set_name("Apple");

echo $apple->name;
?>
```
2 - fora da classe (mudando diretamente o valor da propriedade)

```
<?php
class Fruit {
  public $name;
}
$apple = new Fruit();
$apple->name = "Apple";

echo $apple->name;
?>
```

## A palavra chave instanceof

Voce pode usar a palavra chave `instanceof` para checar se um objeto pertence a uma classe especifica

```
<?php
$apple = new Fruit();
var_dump($apple instanceof Fruit);
?>
```

> texto retirado e livremente traduzido de <a href='https://www.w3schools.com/php/php_oop_classes_objects.asp'>https://www.w3schools.com/php/php_oop_classes_objects.asp</a>


Anterior: [Funções](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/03-Functions.md)
Proximo: [Interfaces](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/05-Interfaces.md)
