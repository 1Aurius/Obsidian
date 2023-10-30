## Primeiramente…

Como já deves ter lido, o ficheiro .env no teu projeto é o que guarda os valores da conecção MYSQLI,aqui estão eles por default:

```json
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```

## Como criar uma nova base de dados utilizando Laravel?

pode-se fazer isso?!

Sim, pode-se, utilizando o comando `**php artisan** migrate` .

Quando corremos dito comando em uma base de dados não existente como a `**laravel`** vamos receber um aviso que ela não existe e se a queremos criar…

Ao dizer-mos que sim,não só o `**laravel`** vai criar a **base de dados** mas tambem vai criar as **tabelas necessarias** !

## PHP MIGRATE

### **O que é que isto quer dizer?**

No nosso projeto há uma pasta `**database**` que dentro de si tem a pasta `**migrations`.**

Dentro de esta pasta temos ficheiros php com nomes no seguinte modelo:

**`TIME_STAMP."_create_".NomeDaTabela.”_table”.php`**

---

## Ao executar a migration

ao executar a migration, o laravel vai ler todos os ficheiros migration e criar a base de dados de acordo com as especificações.

Podemos ver que foram criadas as tabelas default para a auth do breeze.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f20e55c2-be48-4ca2-9a93-496062b59962/Untitled.png)

---

## E se eu quiser modificar a base de dados?

bro, laravel got your back.

Vamos utilizar o comando `**php artisan** make:migration` e a modificação que queremos fazer.

Neste caso vamos fazer: `**php artisan** make:migration update_user_table_name_to_username`

Ao utilizar-mos este comando é criada uma nova migration que ira conter o seguinte(segundo o nosso exemplo):

```php
<?php

use Illuminate\\Database\\Migrations\\Migration;
use Illuminate\\Database\\Schema\\Blueprint;
use Illuminate\\Support\\Facades\\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::table('username', function (Blueprint $table) {
            //
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::table('username', function (Blueprint $table) {
            //
        });
    }
};
```

---

## Ao correr php migrate…

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5623f5b7-8eea-48af-bc5d-7223d8218874/Untitled.png)

Ao correr este comando com a nossa **migration** nova é adicionada mais uma entrada na tabela **migrations**. A **batch** tem um valor diferente porque foi criada em uma **migração diferente**.

### Segundo a decumentação oficial..

As migrations são como o schema de uam base de dados mysql partida em diferentes ficheiros.

---

### Vamos usar a `**migration 2014_10_12_000000_create_users_table.php**`

Aqui vemos um metodo up() que retorna void que chama Schema…

```php
public function up()
    {
        Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });
    }
```

Com esta syntax podemos verificar varias coisas:

### >Schema::create

este metodo estatico de Schema é o que cria a tabela em si, este recebe o nome da tabela ‘users’ neste caso e a blueprint.

### >$table→id()

depois de olhar por dentro deste metodo vemos que ele cria um BIGINT autoincrement, o que é ideal para o id() e a maneira como o faz é incrivel, ele é montado as “peças”.

`**id()←bigIncrements()←unsignedBigInteger()←bigInteger()←addColumn()←**`

**`addColumnDefinition()`**

---

## Analise do examplo:

O nosso objetivo é mudar o “`name`” para “`username`” então temos de colocar uma linha de código para fazer com que isso aconteça:

`$table→renameColumn(’name’,’username’);`

Mas, sempre que fazemos algo para o up() temos de fazer o oposto para o down() logo, no down seria:

`$table→renameColumn(’username’,’name’);`

Podemos ver que temos dois metodos criados, “up()” e “down()” como refere no comentario up().

---

## E agora?

agora que temos a nossa migration de modificação completa podemos correr `**php artisan migrate` e vemos que a nosssa coluna foi modificada :).**

---

## ATENÇÃO

se estiveres com as seguintes versões(ou a migration estiver a dar erros que não fazem sentido):

- MySQL < **`8.0.3`**
- MariaDB < **`10.5.2`**
- SQLite < **`3.25.0`**

tens de fazer `**php composer require doctrine/dbal**`

## Como fazer querys sql simples em Laravel?

para fazer querys sql, podemos utilizar o DB fornecido pelo facade. Para acessar-mos este BD podemos colocar:

### **`use Illuminate\\Support\\Facades\\DB`**

Agora que temos o Acesso BD podemos fazer o nosso query da seguinte forma:

`**dd(DB::select("Select * from users"));**`


Aqui temos o resultado da nossa query no dd.

## Como fazer querys sql parametrizadas em Laravel?

Bastante simples na verdade, seguimos os passos anteriores mas na query fazemos um prepared statement:

`**dd(DB::select("Select * from users where id=?",[1]));**`

Então como podes ver, temos de os fazer da seguinte maneira:

`DB::tipoDeQuery(”queryParametrizada”,[arrayDeParametros]);`

## Laravel Query Builder

Esta é uma outra maneira de fazer **SQL** querys, inves de escrevermos o **query** todo, podemos utilizar funções pre-feitas. Aqui temos um **select** de todos os **users**→

```
      Aqui temos um exemplo,com um **where clause**→

           Aqui temos um exemplo,de um **insert**→
```

```php
$users = DB::table('users')->get();
```

```php
$users = DB::table('users')->where('id',1)->get();
```

```php
$users = DB::table('users')->insert([
        'name'=>'jon',
        'email'=>'jhon@gmail.com',
        'password'=>'jhonPork',
    ]);
```

o update é intuitivo…

## O verdadeiro poder do Query Builder

A verdadeira utilidade o Query Builder chega quando precisamos de algo mais especifico e uma das suas muitas funções extra entram em ação.

## Exemplo do first()

```php
$users = DB::table('users')->first();
```

Aqui vemos que enves de termos um get() temos um first() que apenas devolve o primeiro array.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2579c12f-c354-418d-b8d9-9c5ec8ce00d1/Untitled.png)

## Exemplo do value()

```php
$users = DB::table('users')->value('name');
```
