# Functions (Funções)

O PHP tem mais de 1000 funções incorporadas que podem ser chamdas diretamente dentro de um script para executar uma tarefa especifica, adicionalmente voce pode criar as suas próprias funções customizadas.
Uma função é um bloco de declarações que podem ser utilizadas repetidamente em um programa, não são executadas automaticamente quando a página carrega mas são executadas por um chamado de função.

## Criando uma função no PHP

As declarações de função começam com a palavra `function`

```
<?php

function functionName() {
  codigo a ser executado;
}
```
Um nome de função deve iniciar com uma letra ou underline(_), nomes de funçao não são 'case sensitive'.
Voce deve nomea-la  de forma que ela reflita o que faz.

No exemplo abaixo, criamos uma função chamada "writeMsg()". O código da função inicia no primeiro colchete e termina no ultimo. Essa função escreve "ola mundo" e para chama-la basta escrever seu nome seguido por parenteses:

```
<?php
function writeMsg() {
  echo "ola mundo";
}

writeMsg(); // chamando a função
?>
```

## Argumentos de função do PHP

Informações podem ser passadas para funções através de argumentos. Um argumento é como um variavel.
Argumentos são especificados depois do nome da função dentro dos parenteses. Voce pode adicionar quantos argumentos quiser, somente os separe por virgula

O exemplo seguinte tem uma função com apenas um argumento ($fname). Quando a função familyName() é chamda, tambem passamos junto um sobrenome que será usado dentro da função que mostra vários nomes mas apenas um sobrenome:

```
<?php
function familyName($fname) {
  echo "$fname Refsnes.<br />";
}
familyName("jane");
familyName("hebe");
familyName("stanley");
familyName("kaio");
familyName("roger");
?>
```

No exemplo seguinte a função tem dois argumentos ($fname e $ano)

```
<?php
function familyName($fname, $ano) {
  echo "$fname Refsnes. Nascido em $ano <br />;
}

familyName("joão", "1923")
familyName("maria", "1975")
familyName("otario", "1987")
?>
```

## PHP é uma liguagem pouco tipada

No exemplo anterior voce deve ter observado que não é preciso dizer ao PHP qual o tipo de dados vamos passar na variavel.
O PHP automaticamente associa um tipo de dados à variavel, dependendo do seu valor. Desde tipos de dados não sejam estritamente setados, voce pode fazer coisas como adicionar uma `string` ou um `integer` sem causar um erro.
No PHP 7, tipos de declaração foram adicionados. Isso nos da a opção de especificar o tipo de dados quando declaramos uma função e adicionando a declaração `strict`, retornará "erro fatal" se o tipo de dados não coincidir.

No exemplo a seguir tentamos enviar tanto um `number` quanto uma `string` na função sem usar `strict`

```
<?php
function addNumbers(int $a, int $b) {
  return $a + $b;
}

echo addNumbers(5, "5 days");
// já que o strict não foi abilitado, "5 dias" é tratado com int(5).
// a função retornará 10
?>
```
Para especificar `strict` precisamos setar `declare(strict_types=1)` na primeira linha do arquivo PHP.

No exemplo a seguir, tentamos enviar tanto um `number` quanto uma `string` para a função, mas adicionamos `strict` na declaração

```
<?php declare(strict_types=1);

function addNumbers(int $a, int $b) {
  return $a + $b;
}

echo addNumbers(5, "5 days");
// já que o strict foi abilitado, "5 dias" não é tratado como integer.
// um erro será mostrado
?>
```

### O valor de argumento padrão do PHP

O exemplo a seguir mostra como utilizar um parametro como padrão, se chamamos a função setHeight() sem argumentos ela pega o valor padrão como argumento

```
<?php declare(strict_types=1); // strict é requerido
function setHeight(int $minheight = 50) {
  echo "A altura é: $minheight <br />";
}

setHeight(350);
setHeight(); // usará o valor padrão de 50
setHeight(135);
setHeight(80);
```

### Retornando valores de função

Para que uma função retorne um valor, use a declaração `return`

```
<?php declare(strict_types=1); // strict é requerido
function sum(int $x, int $y) {
  $z = $x + $y;
  return $z;
}

echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "7 + 13 = " . sum(7, 13) . "<br>";
echo "2 + 4 = " . sum(2, 4);
?>
```

### Tipos de retorno de declarações

O PHP 7 tambem suporta tipos de declaração para o `return`, assim como os tipos de declaração para funçoes, habilitar a requisição `strict` vai retornar um erro fatal caso os tipos não coincidam.
Para declarar um tipo de retorno de função, adicione dois pontos(:) e o tipo logo depois de abrir o cochete quando declarar a função.

No seguinte exemplo especificamos um tipo de retorno para a função

```
<?php declare(strict_types=1); // strict é requerido
function addNumbers(float $a, float $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
?>
```
voce pode especificar um tipo de retorno diferente qua não sejam tipos de argumento, mas tenha certeza que esta retornando o tipo correto

```
<?php declare(strict_types=1); // strict é requerido
function addNumbers(float $a, float $b) : int {
  return (int)($a + $b);
}
echo addNumbers(1.2, 5.2);
?>
```

## Passando argumentos pela referencia

No PHP, argumento são usualmente passados como valor, o que significa que uma copia do valor é usado na função e a variavel que foi passada na função não pode ser mudada
Quando um argumento de função é passado pela referencia, mudanças no argumento tamvem mudam a variavel que foi passada.

Para mudar o argumento de função para uma referencia use o operador `&`

```
<?php
function add_five(&$value) {
  $value += 5;
}

$num = 2;
add_five($num);
echo $num;
?>
```

> texto retirado e livremente traduzido de <a href="https://www.w3schools.com/php/php_functions.asp">https://www.w3schools.com/php/php_functions.asp</a>

Anterior: [Estruturas de controle](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/02-Control-Structures.md)
Proximo: [Classes](https://github.com/Unix-User/RoadMap-de-estudos-PHP/blob/main/04-Classes.md)
