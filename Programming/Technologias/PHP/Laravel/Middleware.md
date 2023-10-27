Middleware oferece uma maneira conveniente de verificar e filtrar HTTP requests na tua aplicação.

Um exemplo disto é algo bastante básico como `if(!isset($_SESSION[’user_id’])){header(…)}`,mas aqui é bastante mais avançado.

## Como defenir um MiddleWare?

Usando o comando:

**`php artisan make:middleware EnsureTokenIsValid`**

Este comando cria uma nova classe **`EnsureTokenIsValid`** na diretoria **`app/Http/Middleware`.**

---

No nosso exemplo, fazemos uma verificação se o `‘token’` não for igual a `'my-secret-token'`, o middleware vai returnar um **HTTP** redirect, caso contrario, retorna **$next**(**$request**) para o proximo middleware fazer as suas proprias verificações.

TLDR: Middleware são camadas que o HTTP tem de passar antes de chegar a aplicação.

```php
<?php

namespace App\\Http\\Middleware;

use Closure;
use Illuminate\\Http\\Request;

class EnsureTokenIsValid
{
    public function handle(Request $request, Closure $next)
    {
				if ($request->input('token') !== 'my-secret-token') {
            return redirect('home');
        }
        return $next($request);
    }
}
```

## Global Middleware

Se quiseres que o teu middleware corra sempre que haja uma HTTP request,coloca a tua classe no array $middleware.

## Middleware to routes

Se quiseres que o teu middleware corra sempre que o utilizador estiver em uma certa route,podes fazer o seguinte:

### Apenas um middleware

```php
use App\\Http\\Middleware\\Authenticate;
 
Route::get('/profile', function () {
    // ...
})->middleware(Authenticate::class);
```

### Varios Middleware

```php
Route::get('/', function () {
    // ...

})->middleware([First::class, Second::class]);
```

## Por conveniencia…

podes colocar o teu middleware no array de `$routeMiddleware` no ficheiro `Kernel.php` e fazer um alias ao teu middleware

### Exemplo do array

```php
protected $routeMiddleware = [
        'auth' => \\App\\Http\\Middleware\\Authenticate::class,
        'auth.basic' => \\Illuminate\\Auth\\Middleware\\AuthenticateWithBasicAuth::class,
        'auth.session' => \\Illuminate\\Session\\Middleware\\AuthenticateSession::class,
        'cache.headers' => \\Illuminate\\Http\\Middleware\\SetCacheHeaders::class,
        'can' => \\Illuminate\\Auth\\Middleware\\Authorize::class,
        'guest' => \\App\\Http\\Middleware\\RedirectIfAuthenticated::class,
        'password.confirm' => \\Illuminate\\Auth\\Middleware\\RequirePassword::class,
        'signed' => \\App\\Http\\Middleware\\ValidateSignature::class,
        'throttle' => \\Illuminate\\Routing\\Middleware\\ThrottleRequests::class,
        'verified' => \\Illuminate\\Auth\\Middleware\\EnsureEmailIsVerified::class,
    ];
```

Quando este for defenido podes apenas fazer:

```php
Route::get('/profile', function () {
    // ...
})->middleware('auth');
```

## Middleware Groups

Inves de chamarmos muitos Middleware que normamelmente estão sempre agrupados, podemos fazer um middleware group. Estes podem ser feitos no `Kernel.php` ****no array `**$middlewareGroups`.**

### Exemplo

```php
protected $middlewareGroups = [
        'web' => [
            \\App\\Http\\Middleware\\EncryptCookies::class,
            \\Illuminate\\Cookie\\Middleware\\AddQueuedCookiesToResponse::class,
            \\Illuminate\\Session\\Middleware\\StartSession::class,
            \\Illuminate\\View\\Middleware\\ShareErrorsFromSession::class,
            \\App\\Http\\Middleware\\VerifyCsrfToken::class,
            \\Illuminate\\Routing\\Middleware\\SubstituteBindings::class,
        ],

        'api' => [
            // \\Laravel\\Sanctum\\Http\\Middleware\\EnsureFrontendRequestsAreStateful::class,
            'throttle:api',
            \\Illuminate\\Routing\\Middleware\\SubstituteBindings::class,
        ],
    ];
```

### E se quiseres excluir um Middleware de um grupo para uma certa pagina?

```php
Route::get('/profile', function () {
        // ...
    })->withoutMiddleware([EnsureTokenIsValid::class]);
```

ao utlizar `withoutMiddleware` o middleware EnsureTokenIsValid será excluido.

## Sorting Middleware

Em casos especificos podes querer fazer com que certos middleware tenham prioridadea outros e isto pode ser feito por default com o array **`$middlewarePriority` no** `Kernel.php` , este array pode não existir por default mas se precisares mesmo dessa Organização podes cria-lo.

## Parametros do Middleware

mantendo o tema simples, os nosso middleware podem receber parametros.

### Exemplo:

```php
public function handle(Request $request, Closure $next, string $role): Response
    {
        if (! $request->user()->hasRole($role)) {
            // Redirect...
        }
 
        return $next($request);
    }
```