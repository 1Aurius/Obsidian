([LINK](https://laravel.com/docs/10.x/eloquent))

### Syntax

```php
$users = \\App\\Models\\User::all();
```

Exemplo para select *

```php
$users = \\App\\Models\\User::where('id',2)->get();
```

Exemplo para select com where

```php
$users = \\App\\Models\\User::find(1);
    $users->delete();
```

Exemplo de um delete com um find(procura entries pelo id)

---

```php
$users = \\App\\Models\\User::create([
        'name'=>'joe',
        'email'=>'joe@gmail.com',
        'password'=> bcrypt('joestuff'),
    ]);
```

aqui temos um exemplo de um create, incluindo encriptação de palavra passe.

## O que é?

Eloquent é um object-relational mapper(ORM), ou seja, um criador de classes modelo para as tuas tabelas BD.

```php
$users = \\App\\Models\\User::create([
        'name'=>'jon',
        'email'=>'jhon@gmail.com',
        'password'=>'jhonPork',
    ]);
```

Exemplo para um create

```php
$users = \\App\\Models\\User::where('id',1)->update([
        'email'=>'silly@gmail.com',
    ]);
```

Exemplo para um update

## Eloquent - Mutators

Mutators são metodos que pertencem a classe que representa uma tabela MYSQL no caso de Eloquent. Estes funcionam como Setters da classe modelo.

### A não usar Mutators.

```php
$users = \\App\\Models\\User::create([
        'name'=>'joe',
        'email'=>'joe@gmail.com',
        'password'=> bcrypt('joestuff'),
    ]);
```

### A usar Mutators.

```php
$users = \\App\\Models\\User::create([
        'name'=>'joe',
        'email'=>'joe@gmail.com',
        'password'=>'joestuff'
    ]);
```

Podemos ver que a função bcrypt() encrypta o valor ‘joestuff’ para hash, mas nós queremos que isso esteja por default então na classe modelo User.php vamos adicionar o seguinte:

```php
protected function password(): Attribute
{
returnAttribute::make(
        set:fn($value) => bcrypt($value),
    );
}
```

### Troubleshooting

caso o metodo não funcione, pode ser por causa de estarmos a user o ficheiro atributes errado, então tem acerteza que no topo do teu código tens algo como isto:

```php
use Illuminate\\Database\\Eloquent\\Casts\\Attribute;
```

## Eloquent - Acessor

Estes seriam os getters da classe modelo.Vamos dizer que precisamos do nome em UPPERCASE do utilizador com

id = 2.

### A não usar Acessors.

```php
$users=User::find(2);

    dd(strtoupper($users->name));
```

Usamos a função strtoupper para fazer com que a string tenha todos os carateres em UPPERCASE

---

Podemos ver que no metodo acima dos mutators temos um `**set:**`, aqui temos o `**get:**`. Podemos ver que ao value é aplicado a função strtoupper.

### A usar Acessors.

```php
$users=User::find(2);

    dd($users->name);
```

Para fazer com que o nome saia sempre em UPPERCASE temos de fazer o seguinte metodo:

```php
protected functionname(): Attribute
{
returnAttribute::make(
        get:fn($value) =>strtoupper($value),
    );
}
```