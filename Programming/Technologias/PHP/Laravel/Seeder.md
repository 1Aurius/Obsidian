## Introdução

Seeding é uma habilidade do Laravel capaz de criar registos de teste ao comando.

Ao criarmos uma classe seed com o comando make:seeder este primeiro cria nomeDaSeed.php em `database>seeders>nomeDaSeed.php` com um template default como apresentado ao lado→

Uma classe seeder tem um metodo run() por default, este deve ser editado para servir as necessidades do programador.

Este comando é utilizado quando se corre o comando

**`php artisan db:seed`**

Dentro deste podemos colocar inserts para a nossa base de dados,criando assim um metodo capaz de criar registos de teste.

## Como criar um Seeder?

para criar um seeder novo usamos o comando:

```php
php artisan make:seeder UserSeeder
```

### Exemplo

```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

classUserSeederextendsSeeder
{
/**
     * Run the database seeds.
     */
public function run():void
{
//
}
}

```

## Exemplo final

```php
<?php
 
namespace Database\\Seeders;
 
use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Hash;
use Illuminate\Support\Str;
 
class DatabaseSeeder extends Seeder
{
    /**
     * Run the database seeders.
     */
    public function run(): void
    {
        DB::table('users')->insert([
            'name' => Str::random(10),
            'email' => Str::random(10).'@gmail.com',
            'password' => Hash::make('password'),
        ]);
    }
}
```