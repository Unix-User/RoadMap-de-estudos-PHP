# Data Types (tipos de dados em PHP)

No PHP as Variaveis podem armazenar dados de diferentes tipos e tipos de dados podem fazer diferentes coisas.
Nesse documento discutiremos alguns pontos sobre os tipos de dados são suportados pelo PHP.
O PHP suporta os seguintes tipos de dados:

- String
- Integer
- Float
- Boolean
- Array
- Object
- NULL
- Resource

# String

Uma string é uma sequencia de caracteres como "Hola mundo".
Uma string pode ser qualquer texto "ENTRE ASPAS", Voce pode usar aspas simples ou duplas;

## Exemplo

```
<?php echo "hello Word" ?>

```

# Integer

Um tipo de dado integer(integro) é um numero não decimal entre -2, 147, 483, 648 e 2, 147, 483, 674.
Regra para integers:

  - um integer dever ter no minimo um digito
  - um integer não pode ter um ponto decimal
  - um integer pode ser tanto positivo ou negativo
  - integers podem ser especificados em:
      - decimal(base 10)
      - hexadecimal(base 16)
      - octal(base 8)
      - ou notação binaria(base 2)

No seguinte exemplo $x é um integer. A função `var_dump()` retorna o tipo de dados e valor

## Exemplo

```
<?php  
$x = 85;
var_dump($x);
// isso vai retornar int(85)
?>
```

# Float

Um float (número de ponto flutuante) é um numero com um ponto decimal ou um numero em formato exponencial.

no exemplo seguinte %x é um `float`. A função `var_dump()` do PHP vai retornar os tipos de dados e valores:

## Exemplo

```
<?php
<?php  
$x = 10.365;
var_dump($x);
// isso vai retornar float(10.365)
?>
```

# Bolean

Um valor Boleano representa dois possiveis estados: `TRUE`(verdadeiro) ou `FALSE`(Falso)

```
$x = true;
$y = false;
```
Boleanos são amplamente utilizados em testes condicionais. Voce aprendera mais sobre testes condicionais adiante nesse tutorial.

# Array

Um `array` armazena multiplos valores em uma unica variável.

No seguinte exemplo `$carros` é um `array`. A função `var_dump()` do PHP vai retornar os tipos de dados e valores:

```
<?php  
$carros = array("Volvo","BMW","Toyota");
var_dump($carros);
/** isso vai retornar **/
/*
array(3) {
  [0]=>
  string(5) "Volvo"
  [1]=>
  string(3) "BMW"
  [2]=>
  string(6) "Toyota"
}
*/
?> 
```

Voce vai aprender muito mais sobre arrays em outra oportunidade nesse tutorial.

# Object

Classes e `objects`(objetos) são dois dos aspectos principais da programação orientada a objetos.

Uma `class` é um template para `objects`, e um `object` é uma instancia de uma `class`.

Quando objetos individuais são criados, eles herdam todas as propriedades e comportamentos da classe, mas cada objeto tem diferentes valores e propriedades.

Vamos assumir que temos uma classe chamada carro. Um carro tem propriedades, como modelo, cor, ano, etc. Nos podemos definir nessa classe as variaveis como $modelo, $cor, e etc para armazenar os valores dessas propriedades.

Quando voce criar os objetos(Volvo, BMW, Toyota, etc), elas terão herdado todas a propriedades e comportamentos da classe, mas cada objeto terá seus próprios valores para cada proprieade.

Se voce criar uma função `__construct()`, o PHP automaticamente chama essa função quando voce cria um objeto a partir de uma classe.

## Exemplo

```

<?php
class Carro {
  public $cor;
  public $modelo;
  public function __construct($cor, $modelo) {
    $this->cor = $cor;
    $this->modelo = $modelo;
  }
  public function message() {
    return "Meu carro é um " . $this->cor . " " . $this->model . "!";
  }
}

$myCar = new Carro("Vermelho", "Astra");
echo $myCar -> message();
echo "<br>";
$myCar = new Carro("Cinza", "Chevete");
echo $myCar -> message();
?>
/* Isso vai retornar
My car is a black Volvo!
My car is a red Toyota!
*/
```

# O valor NULL

NULL é um dado especial que tem apenas um valor NULO!

Uma variavel com o tipo de dados `null` é uma variavel que não tem valor definido.
Se uma variavel é setada sem ter um valor definido seu valor é automaticamente `null`
Ela tambem pode ser utilizada para esvaziar uma variavel e a definindo como `null`

## Exemplo

```
<?php
$x = "ola mundo";  // variavel $x contem "ola mundo"
$x = null;  // Variavel agora esta vazia
var_dump($x);  // isso retorna NULL
?>
```

# Resource

O tipo especial `resource` não é exatamente um tipo de dado. Ele armazena referencias a funções e recursos externos ao PHP.
Um exemplo de uso desse tipo de dados são as chamadas nos bancos de dados. Falaremos disso adiante.


> texto retirado e livremente traduzido de https://www.w3schools.com/php/php_datatypes.asp
