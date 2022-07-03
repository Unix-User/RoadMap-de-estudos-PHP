# Implementação do PHP, Classes abstratas e Interfaces

## Classes abstratas
Uma classe abstrata contem pelo menos um metodo abstrato, que é o metodo sem nenhum codigo nela, somente o nome e os parametros, e que foi marcada como abstrata
O propósito é prover um tipo de modelo para herdar e do qual as classes herdeiras implementarão os metodos abstratos

```
<?php
abstract class AbstractClass
{
    // abtract method defined
    abstract protected function name();
    abstract protected function age();
    abstract protected function profession($sex);
    // In abstract Class we can also define common method also.
    public function getName(){
     return $this->name();
    }
}
class ManClass extends AbstractClass
{
    protected function name() {
        return "Faysal Ahmed";
    }
public function age() {
        return 35;
    }
public function profession($sex){
     switch ($sex) {
      case 'male':
       $profession = "Engineer";
       break;
      case 'female':
       $profession = "Doctor";
       break;
      default:
       $profession = "Teacher";
       break;
     }
     return $profession;
    }
}
class WomanClass extends AbstractClass
{
    protected function name() {
        return "Amie Jackson";
    }
public function age() {
        return 25;
    }
public function profession($sex){
     switch ($sex) {
      case 'male':
       $profession = "Engineer";
       break;
      case 'female':
       $profession = "Doctor";
       break;
      default:
       $profession = "Teacher";
       break;
     }
     return $profession;
    }
}
$manClass = new ManClass();
$manName = $manClass->getName();
$manAge = $manClass->age();
$manProfession = $manClass->profession("male");
echo "{$manName} is a {$manAge} years old & an {$manProfession}</br>";
$womanClass = new WomanClass();
$womanName = $womanClass->getName();
$womanAge = $womanClass->age();
$womanProfession = $womanClass->profession("female");
echo "{$womanName} is a {$womanAge} years old & an {$womanProfession}";
?>
```
No codigo acima, Faysal Ahmed é um engenheiro de 35 anos, Amie Jackson é uma médica de 25 anos
Então, em uma classe abstrata devemos definir pelo menos um metodo abstrato dentro da classe abstrata, mas tambem podemos definir metodos comuns dentro das classe abstratas.

## PHP Interfaces:
No PHP, os blocos de interface que declaram conjunto de funções a serem definidas com uma classe para implementar essa interface. Uma classe pode estender mais de uma interface, assim, podemos simular várias heranças em PHP. As interfaces são definidas da mesma forma que uma classe, mas com a palavra-chave da interface substituindo a palavra-chave da classe e sem nenhum dos métodos tendo seus conteúdos definidos. Para implementar uma interface, o operador de implementos é usado. Todos os métodos na interface devem ser implementados dentro de uma classe; não fazê-lo resultará em um erro fatal. As classes podem implementar mais de uma interface se desejar separando cada interface com uma vírgula.

```
<?php
// Declare the interface 'iTemplate'
interface iTemplate
{
    public function setVariable($name, $var);
    public function getHtml($template);
}
// Implement the interface
// This will work
class Template implements iTemplate
{
    private $vars = array();
  
    public function setVariable($name, $var)
    {
        $this->vars[$name] = $var;
    }
  
    public function getHtml($template)
    {
        foreach($this->vars as $name => $value) {
            $template = str_replace('{' . $name . '}', $value, $template);
        }
 
        return $template;
    }
}
// This will not work
// Fatal error: Class BadTemplate contains 1 abstract methods
// and must therefore be declared abstract (iTemplate::getHtml)
class BadTemplate implements iTemplate
{
    private $vars = array();
  
    public function setVariable($name, $var)
    {
        $this->vars[$name] = $var;
    }
}
```

As interfaces se assemelham a classes abstratas na qual incluem métodos abstratos que o programador deve definir nas classes que herdam da interface. Dessa forma, as interfaces contribuem para a organização do código porque comprometem as classes infantis a métodos abstratos que devem implementar. O uso de interfaces torna-se muito útil quando trabalhamos em uma equipe de programadores e queremos garantir que todos os programadores escrevam os métodos em que devem trabalhar, ou mesmo no caso de um único programador que queira se comprometer a escrever determinados métodos nas classes infantis.

Podemos implementar uma série de interfaces na mesma classe, e assim contornar a lei que proíbe a herança de mais de uma classe dos pais. Para demonstrar várias heranças de diferentes interfaces, criamos outra interface, o Vehicle, que compromete as classes que a implementam a uma propriedade $hasWheels booleana.

```
interface Vehicle {
  public function setHasWheels($bool); 
  public function getHasWheels();
}
class miniCar implements Car, Vehicle {
  private $model; 
  private $hasWheels; 
  
  public function setModel($name)
  { 
    $this -> model = $name; 
  }
  
  public function getModel()
  {
    return $this -> model; 
  }
  
  public function setHasWheels($bool)
  { 
    $this -> hasWheels = $bool; 
  }
  
  public function getHasWheels()
  {
  return ($this -> hasWheels)? "has wheels" : "no wheels";
  }
}
```

Ponto-chave das interfaces:

- As interfaces podem incluir métodos e constantes abstratas, mas não podem conter métodos e variáveis concretas.
- Todos os métodos na interface devem estar no escopo da visibilidade pública.
- Uma classe pode implementar mais de uma interface, enquanto pode herdar de apenas uma classe abstrata.

  > texto retirado e livremente traduzido de <a href="https://medium.com/oceanize-geeks/implementation-of-php-abstract-class-interfaces-a271d57cd8a6">https://medium.com/oceanize-geeks/implementation-of-php-abstract-class-interfaces-a271d57cd8a6</a>
