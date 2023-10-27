ir para onde e quando?

---

### web.php

Aqui usamos funções para definir routes para a nossa web interface

### Exemplo

```php
Route::get('/', function () {
    return view('welcome');
});
```

Por default todas as routes definidas aqui vão ter o web [**middleware**](https://www.notion.so/Middleware-6c5d83644bb24dd2a95b7ae2746a538c?pvs=21) group aplicado nelas.

## Diving deeper

Então como vimos a cima, se não houver nenhuma pedido get ou post para o html, devolve a blade welcome, ou seja, isto funciona como um index.

## Todos os tipos de Router Methods

O router permite registar routes que correspondem a todos os tipos de HTTP verb.

- **Route::get($uri, $callback);**
- **Route::post($uri, $callback);**
- **Route::put($uri, $callback);**
- **Route::patch($uri, $callback);**
- **Route::delete($uri, $callback);**
- **Route::options($uri, $callback);**

---

### Ver as Routes

se a tua route só precisa de devolver uma view, podes usar `Route::view`, tal como o `redirect`, este metodo permite um shortcut para não teres de declarar a route inteira ou o controlador.Caso queiras adicionar data podes fornecer um array como o terceiro argumento.

### Com `Route::view`

```php
Route::view('/','welcome')
```

### Sem // //

```php
Route::get('/', function () {
    return view('welcome');
});
```

Podes ter reparado que o argumento da função `**view()`** é apenas welcome, isto é porque a extensão **`.blade.php`** já é adicionada automaticamente, assim encontrando o ficheiro com sucesso.

### outro exemplo:

```php
**Route::get('/user', [UserController::class, 'index']);**
```

se a route from /user então vamos aplicar o middleware Usercontroller e receber a view index(not sure abt the index part).

---

Caso seja necessario podes fazer com uma route responda a varios HTTP verbs, nesse caso podes usar o `match method` e caso queiras que responda a todos usas `any method`.

## Redirect Routes

se quiseres redirecionar o utilizador para outro URL, podes usar **`Route::redirect`.**

### exemplo:

```php
Route::redirect('/here', '/there',301);
```

aqui vemos que temos 2 parametros sendo estes obrigatorios e depois temos um status code que por default é 302, aqui declaramo-lo como 301.

---

## Route List

Caso queiras ver todas as routes da aplicação podes utilizar o comando **`route:list` e ao adicionar `-v`** ao comando podes ver todos os middleware utlizados em cada route.

### Exemplo

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9713e03b-0d35-43ad-9c2d-6fa77fb916c8/Untitled.png)

---

## Parametros das Routes

### Required parameters

Por vezes teras de apanhar valores do URL da tua route. Por exemplo, user’s ID, então seria feito desta maneira:

```php
Route::get('/user/{id}', function (string $id) {
    return 'User '.$id;
});
```

Para ter varios valores seria da seguinte forma:

```php
Route::get('/posts/{post}/comments/{comment}', function (string $postId, string $commentId) {
    // ...
});
```

### Optional Parametes

Ocasionalmente podes precisar de valores no URL quen nem sempre estarão presentes, então usamos optional Parameters da seguinte forma:

```php
Route::get('/user/{name?}', function (string $name = null) {
    return $name;
});
 
Route::get('/user/{name?}', function (string $name = 'John') {
    return $name;
});
```

neste caso o `string $name = null` define o valor default como nulo.

### ****Regular Expression Constraints****

Talvez precises que o valor que vais retirar do teu URL seja de um formato especifico, nesses casos podes utilizar o where method, este restringe o formato do valor , como é mostrado no exemplo asseguir:

```php
Route::get('/user/{name}', function (string $name) {
    // ...
})->where('name', '[A-Za-z]+');
 
Route::get('/user/{id}', function (string $id) {
    // ...
})->where('id', '[0-9]+');
```

### E se o valor não for conpativel com o formato?

uma resposta 404 http vai ser devolvida.

Podemos ver que temos o

`→where(o valor dentro das brackets,o formato)` .

Temos tambem outros tipos de where methods que permitem que adiciones os teus formatos mais rapidamente, exemplo:

```php
Route::get('/category/{category}', function (string $category) {
    // ...
})->whereIn('category', ['movie', 'song', 'painting']);

Route::get('/user/{name}', function (string $name) {
    // ...
})->whereAlphaNumeric('name');
```

### ****Global Constraints****

se quiseres um valor do URL tenha um formato universal poes usar o metodo Pattern. Este deve ser defenido no boot method na classe **`App\\Providers\\RouteServiceProvider`**

```php
public function boot(): void
{
    Route::pattern('id', '[0-9]+');
}
```

## Name Routes

Ao dar nomes as routes faz com que seja mais conveniente acessa-las, exemplo:

```php
Route::get('/user/profile', function () {
    // ...
})->name('profile');
```

## Gerar Urls para Named routes

```php
// Generating URLs...
$url = route('profile');
 
// Generating Redirects...
return redirect()->route('profile');
 
return to_route('profile');
```

Agora que temos a nossa route com um nome poemos atribuir-le um URL atraves da funções route e redirect do laravel.

Se a tua route tiver parametros a retirar do url podes acidionalos como segundo parametro na função route, exemplo:

```php
Route::get('/user/{id}/profile', function (string $id) {
    // ...
})->name('profile');
 
$url = route('profile', ['id' => 1]);
```

---

## Route Groups

Estes servem para fazer com que um grupo de routes partilhem atributos sem ter de declarar cada um á vez.

---

## Controllers

```php
use App\\Http\\Controllers\\OrderController;
 
Route::controller(OrderController::class)->group(function () {
    Route::get('/orders/{id}', 'show');
    Route::post('/orders', 'store');
});
```

se um grupo de routes usam todos o mesmo controlador podes usar o metodo controller para defenir o mesmo para todos os routes.

### Route Prefixes

(big words lol)