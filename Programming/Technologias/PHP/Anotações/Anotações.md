## namespace

namespace é um qualificador que serve para ambos:

- manter uma melhor organização ao agrupar varias classes que trabalham juntas para completar uma tarefa.
- permitem que duas classes tenham nome diferentes, sempre e quando forem de namespace diferentes.

## use

use em php serve para fazer com que uma classe herde varios metodos para alem daqueles que só podem ser herdados na super-classe.

```php
<?php
trait message1 {
  public function msg1() {
    echo "OOP is fun! ";
  }
}

class Welcome {
  use message1;
}

$obj = new Welcome();
$obj->msg1();
?>
```

## extends Model

em relação a Model, este é o Modelo base para todas as classes Modelo.

A variavel de isntância $table é declarada em Model e é o nome da Tabela mysql á qual a classe representa. Por default, $table é o nome da classe no plural.

## Collection

o que são?([LINK](https://laravel.com/docs/10.x/collections))

Quando vemos o resultado do nosso query, ve-mos que não foi devolvido em apenas um array, mas sim em uma collection.

Uma collection é na verdade uma versão de array modificada pelo laravel que tem mais funções e capacidades que um array normal.

## Aonde é que o Laravel guarda constantes cruciais?

O **laravel** quando cria um projeto, cria um ficheiro chamado .**env**, que guarda todo o tipo de constantes como **mysqli** connects , **mail**,etc….