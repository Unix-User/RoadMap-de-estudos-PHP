# Interfaces

Interfaces lhe permitem especificar qual metodo uma classe deve implementar, elas tornam faceis usar uma variedade de classes do mesmo jeito. Quando uma ou mais classes usam a mesma interface, ela é referida como polimorfismo. Interfaces são declaradas com a palavra chave `interface`

```
<?php
interface InterfaceName {
  public function someMethod1();
  public function someMethod2($name, $color);
  public function someMethod3() : string;
}
?>
```

## Interfaces vs. Classes abstratas

Interfaces são similares a classes abstratas. A diferença entre interfaces e classes abstratas são:

- Interfaces não podem ter propriedades, mas classes abstratas sim.
- Todos os metodos da interfaces devem ser publicos, enquanto os metodos da classe abstrata são publicos ou protegidos
- todos os metodos em uma interfaces são abstratos, entçao eles não podem ser implentados em codigo e a palavra chave abstrata não é nescessária.
- classes podem implementar interfaces enquanto herdam de outra classe ao mesmo tempo

## Usando interfaces

Para implementar uma interface, uma classe deve usar a palavra chave `implements`. Uma classe que implementa uma interface deve implemntar todas os metodos da interface.

```
<?php
interface Animal {
  public function makeSound();
}

class Cat implements Animal {
  public function makeSound() {
    echo "Meow";
  }
}

$animal = new Cat();
$animal->makeSound();
?>
```
No exemplo acima, vamos dizer que nos queremos escrever um software que gerencia um grupo de animais. Existem ações que todos os animais podem fazer, mas cada animal a faz de sua propria maneira. Usando interfaces, podemos escrever codigo que pode trabalhar por todos os animais mesmo se cad animal trabalha diferentemente.

```
<?php
// Interface definition
interface Animal {
  public function makeSound();
}

// Class definitions
class Cat implements Animal {
  public function makeSound() {
    echo " Meow ";
  }
}

class Dog implements Animal {
  public function makeSound() {
    echo " Bark ";
  }
}

class Mouse implements Animal {
  public function makeSound() {
    echo " Squeak ";
  }
}

// Create a list of animals
$cat = new Cat();
$dog = new Dog();
$mouse = new Mouse();
$animals = array($cat, $dog, $mouse);

// Tell the animals to make a sound
foreach($animals as $animal) {
  $animal->makeSound();
}
?>
```

## Explicando o exemplo

Cães, gatos, ratos são todas classes que implementam a interface animal, o que significa que todos eles são aptos a fazer um som usado o metodo `makeSound()`. Por causa disso podemos percorrer por todos os animais e dizer pra fazer um som mesmo se não sabemos qual tipo de animal cada um é. Já que as interfaces não dizem para as classes como implementar o metodo cada animal fara o som de sua propria maneira.

> texto retirado e traduzido livremente de <a href="https://www.w3schools.com/php/php_oop_interfaces.asp">https://www.w3schools.com/php/php_oop_interfaces.asp</a>

Anterior: [Funções](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/04-Classes.md)
Proximo: [Extendendo e Implementando](#)
