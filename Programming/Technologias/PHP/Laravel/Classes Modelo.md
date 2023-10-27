## Exemplo de classes modelo em Laravel.

```php
<?php

namespace App\\Models;

use Illuminate\\Database\\Eloquent\\Model;

class Book extends Model
{
    //awesome code
    protected $table = 'Books';
}
?>

```

## extends Model

em relação a Model, este é o Modelo base para todas as classes Modelo.

A variavel de isntância $table é declarada em Model e é o nome da Tabela mysql á qual a classe representa. Por default, $table é o nome da classe no plural.

## How to generate?
you can use the command ``php artisan make:model [name]`` and it will be put inside ``app/Models`` 
##### Example
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Flight extends Model

{

// ...

}
```

## Table Names
ao criarmos o modelo nós não declaramos a que tabela pertence a classe modelo **Flight**. Por convenção, o modelo vai usar o "snake_case", plural do seu nome a não ser que seja especificado outro nome especifico.
##### Example
+ Flight - modelo
+ flights - nome assumido pelo modelo

---
+ AirTrafficController - Modelo
+ air_traffic_controllers - nome assumido pelo modelo

##### Como especificar o nome da tabela?
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Flight extends Model

{

/**

* The table associated with the model.

*

* @var string

*/

protected $table = 'my_flights';

}
```

## Primary Keys
O modelo vai assumir que a tabela tem uma primary key chamada **ID**, se necessário podemos especificar qual é a primary key da tabela.

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Flight extends Model

{

/**

* The primary key associated with the table.

*

* @var string

*/

protected $primaryKey = 'flight_id';

}
```
### Incrementação
O modelo tambem vai assumir que a chave é um integer e auto-increment. se decidires não utilizar um id com auto-increment podes referir isso á classe modelo.
##### Exemplo
```php
<?php

class Flight extends Model

{

/**

* Indicates if the model's ID is auto-incrementing.

*

* @var bool

*/

public $incrementing = false;

}
```
o mesmo se aplica ao datatype da chave
##### Exemplo
```php
<?php

class Flight extends Model

{

/**

* The data type of the auto-incrementing ID.

*

* @var string

*/

protected $keyType = 'string';

}
```

>[!Atenção]
>Chaves Compostas não são suportadas pelos modelos Eloquent(os que estamos a usar).
## TimeStamps
se não quiseres utilizar [[timestamps]] podes referir isso ao teu modelo pois por default quando crias uma [[migração]] ela vai vir com ```Created at```,``Updated at``.
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Flight extends Model

{

/**

* Indicates if the model should be timestamped.

*

* @var bool

*/

public $timestamps = false;

}
```
se quiseres utilizar uma coluna especifica para registar o ```Created at```,``Updated at``  podes utilizar:
```php
<?php

class Flight extends Model

{

const CREATED_AT = 'creation_date';

const UPDATED_AT = 'updated_date';

}
```