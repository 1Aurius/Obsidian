## Introdução

aqui está passo a passo, com explicações de como aplicar a tecnica AJAX a um projeto laravel.

Escolham um deus e rezem porque esta não é a coisa mais fixe do mundo

Isto foi estudado a partir do ChatGPT btw.

## Passo 1

criar um controlador para tratar dos requests. se ainda não viu os [controllers](https://www.notion.so/Controllers-f10c5b7f199a4eb2a52013ee23e3659f?pvs=21) agora é boa altura.

```php
php artisan make:controller AjaxController
```

```php
<?php

namespace App\\Http\\Controllers;

use Illuminate\\Http\\Request;

class AjaxController extends Controller
{
    public function handleRequest(Request $request)
    {
        // Lide com a requisição AJAX aqui e retorne a resposta
    }
}
```

## Passo 2

criar o [route](https://www.notion.so/Routes-89c8a0633c5640349434e1a8b0171054?pvs=21) no seu ficheiro web.php ou api.php, nese caso funciona em ambos.

```php
Route::get('/ajax/request', 'AjaxController@handleRequest')->name('ajax.request');
```

## Passo 3

agora no seu ficheiro [.blade.](https://www.notion.so/Blade-Templates-0eb450be36d0425a99fc752eef2df76f?pvs=21) pode colocar o código que faz com isto tudo aconteça.

```php
<!-- Inclua a biblioteca do jQuery -->
<script src="<https://code.jquery.com/jquery-3.6.0.min.js>"></script>

<!-- Seu conteúdo HTML -->
<button id="ajaxButton">Enviar Requisição AJAX</button>

<!-- Seu código JavaScript -->
<script>
  $(document).ready(function() {
    $('#ajaxButton').on('click', function() {
      $.ajax({
        url: "{{ route('ajax.request') }}",
        type: "GET",
        data: {
          // Dados adicionais a serem enviados, se necessário
        },
        success: function(response) {
          // Lide com a resposta do servidor aqui
          console.log(response);
        },
        error: function(xhr) {
          // Lide com quaisquer erros que ocorram durante a requisição AJAX
          console.log(xhr.responseText);
        }
      });
    });
  });
</script>
```