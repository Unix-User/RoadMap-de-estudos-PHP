# PHP Control structures

Control structures ou estruturas de controle estão no centro da logica de programação. Elas permitem que um script reaja de forma difretente dependendo do que já ocorreu, ou com base na entrada do usuário, e permitem o manuseio gracioso de tarefas repetitivas.
No PHP, existem dois tipos primarios de estruturas de controle: Declarações condicionais e loops de controle. Vamos dar uma olhada mais de perto neles:

## Conditional statements(declarações condicionais)

As declarações condicionais permitem ramificar o caminho da execução em um script baseado em se uma unica ou multiplas condições forem verdadeiras ou falsas. Simplificando, elas permitem que vc teste as coisas e realize varias ações com base nos resultados.

### if

``` 
<?php
$x=1;
if ($x == 1) print ‘$x is equal to 1’;
?>
```

Esse exemplo ilustra de maneira simples a declaração de um `if`. Essa declaração sempre começa com `if` seguida por uma condição entre parenteses. se a condição for verdadeira então as declarações seguintes serão imediatamente executadas, se no caso acima fosse falso vc veria uma tela em branco no navegador ao rodar o script.

Quando voce possui mais de uma declaração a ser executada na estrutura de controle, e necessario coloca-las entre colchetes:

```
<?php
$x=1;

if ($x == 1) {
   print ‘$x is equal to 1’;
   $x++;
   print ‘now $x is equal to 2’;
}
?>
```

Você também pode incluir várias condições entre parênteses. Para que as declarações aninhadas sejam executadas, todas as condições devem ser avaliadas de forma verdadeira.

```
<?php
$x=1;
if ($x == 1 OR $x == 2) print ‘$x is equal to 1 (or maybe 2)’;
?>
```

### else

Como o nome indica, `else` permitem que você faça "outra coisa" se a condição dentro de uma Declaração `if` for avaliada como falsa:

```
<?php
$x=1;
if ($x == 2) {
print ‘$x is equal to 2’;
} else {
   print ‘$x is equal to 1’;
}
?>
```

### elseif

Até agora, conseguimos responder a uma condição, e fazer algo se essa condição não for verdadeira. Mas que tal avaliar múltiplas condições? Você pode usar uma série de Declarações If para testar cada condição potencial, mas em algumas situações essa não é uma opção adequada😢😢😢... É aqui onde as declarações `elseif` entram!!!

Uma combinação de Declarações de `if` e `else`, Quando uma condição `if` for falsa e chamamos o `elseif`, se esse for verdadeiro então o scrip seguinte será executado, voce não precisa ficar avaliando sequencias de if/else/if/else/if...

```
<?php
$x=1;

if ($x == 2) {
print ‘$x is equal to 2’;
} else if ($x == 1) {
print ‘$x is equal to 1’;
} else {
   print ‘$x does not equal 2 or 1’;
}
?>
```

### switch

O `switch` é uma boa alternativa ao if/elseif/else em situações onde voce quer checar multiplas variáveis contra uma unica variável ou condição. Essa é a sintaxe básica:

```
<?php
$var = "yes";

switch ($var) {
   case "yes":
     print ‘$var is equal to yes’;
break;

   case "no":
     print ‘$var is equal to no’;
     break;
}
?>
```

O `switch` é executado de maneira diferente do if/elseif/else, se o valor avaliado corresponde ao valor da expressão do `switch` todos as declarações seguintes serão executadas, incluindo as dos casos subsequentes.
Para previnir isso deve ser declarar um `break` que finaliza a execução do `switch` e permite que o script continue sua execução, o `break` tambem pode ser usado para encerrar loops.

```
<?php
$var = "yes";

switch ($var) {
   case "maybe":
     print ‘$var is equal to yes’;
break;

   case "no":
     print ‘$var is equal to no’;
     break;
 
   default:
     print ‘none of the other two cases were true, so this sentance will be printed out instead.’;
}
?>
```

A declaração `default` funciona como o `else`  e será executada se nenhum dos outros casos forem atendidos
A declaração `exit` tambem pode ser particularmente util em situações que podem ser consideradas como "erro faltal" ou em qualquer outro momento que voce precisar encerrar a execução do script antes que ele encerre o ciclo predeterminado.

```
<?php
$var = "yes";
switch ($var) {
   case "yes":
     print ‘$var is equal to yes’;
     exit;
   case "no":
     print ‘$var is equal to no’;
     break;
}

print "this will not be printed, because the script will have terminate before this line is reached";
?>
```

## Operadores ternários

Embora técnicamente um operador ternário não seja uma estrutura de controle, o "?" pode ser usado como abreviação para declarações simples de if/else. Ele só pode ser usado em situações em que voce deseja executar uma unica expressão com base em se uma unica condição é verdadeira ou falsa.

```
<?php
$var = "yes";
switch ($var) {
   case "yes":
     print ‘$var is equal to yes’;
     exit;
   case "no":
     print ‘$var is equal to no’;
     break;
}

print "this will not be printed, because the script will have terminate before this line is reached";
?>
```
a condição esta no primeiro set de parenteses, se for verdadeira então a expressão do segundo set de parenteses sera executada, se falso o tercerio set de parenteses sera executado.

## Loops e estruturas de repetição

São instancias para repetição de tarefas no PHP, como requisição e formatação de dados em um banco de dados, enviar emails para uma lista de emails ou trocar o conteudo de um array.

### while

São os mais simples

```
<?php
$x=1;
while ($x <=10) {
   print "$x<br>";
   $x++;
}
?>
```
Quando você roda esse snipet os numeros de 1 a 10 serão escritos na sua tela. Observe o código, de várias maneiras ele é similar ao `if`. Primeiro declaramos o `while` seguido por uma condição cercada por parenteses.
A instrução agrupada entre cochetes sera executada equanto a condição entre parenteses for verdadeira, se ela for falsa então a instrução do loop não será executada.

### do... while

São parecidos com o exemplo anterior

```
<?php
$x=11;
do {
print "$x<br>";
$x++;
} while ($x <=10);?>
```
A principal diferença é a validade de uma condição no `do`, pois o `while` fará o teste após a execução do loop. No exemplo acima o valor de $x seria apresentado apenas uma vez em sua tela e então o loop se encerra porque $x é maior que 10.

### for

```
<?php
for($x=1; $x<=10; $x++) {
print "$x<br>";
}
?>
```
Esse loop avalia três expressões agrupadas entre parenteses. A primeira expressão só é executada uma vez, quando o loop é inicializado, neste caso, $x é criado e lhe é dado um valor. A próxima expressão é uma condição que é verificada cada vez que o loop roda. Uma vez que a condição é falsa, o loop vai parar de executar. Assim como o loop de tempo `while`,  se a condição for considerada falsa na primeira corrida, nenhuma das instruções dentro do loop será executada. A expressão final será executada cada vez que o loop validar as declarações aninhadas anteriormente.

### foreach

```
<?php
/* suponhamos que temos registros de carros e detalhes de cada um
 * em uma tabela de um banco de dados, voce pode chamar o objeto e lista-los
 * com todos os detalhes com o seguinte codigo
 */
 
foreach($carros as $carro) {
print "$carro->nome<br>";
print "$carro->cor<br>";
}
?>
```
Este novo loop foi introduzido na versão PHP 4. É usado exclusivamente para looping através de elementos de uma matriz, permitindo que você imprima facilmente ou execute operações em elementos dentro de uma matriz.

  > texto retirado e traduzido livremente de <a href="https://www.developer.com/languages/php/php-control-structures/#:~:text=There%20are%20two%20types%20of,indented%20for%20the%20same%20reason.">https://www.developer.com/languages/php/php-control-structures/#:~:text=There%20are%20two%20types%20of,indented%20for%20the%20same%20reason.</a>
