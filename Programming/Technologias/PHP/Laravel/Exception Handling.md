## Introdução

Quando crias um novo projeto no Laravel por default são feitas Exception Handlers no **`App\Exceptions\Handler`**,estas são responsaveis por fazer log e processo da exception para o utilizador **.**Caso queiras criar uma ****Exception Handler personalizada, aqui está como faze-lo.

## Configuração

a opção de debug no ficheiro de configuração `config/app`.php determina quanta informção vai ser mostrada ao utilizador em caso de erro.

Por default esta opção respeita o valor de `APP_DEBUG` ,este está guardado no .env file.

## The exception Handler

qualquer excessão é processada pela classe `App\Exceptions\Handler` . Esta classe contem o metodo `register` onde se pode preparar reportes de excessões customizados.

exceptions vão ser logadas a partir da tua logging option,fazendo isso completamente livre de escolha.

Se precisares de reportar um tipo especifico de exception podes utilizar o metodo reportable, este vai ler o type-int da excessão e correr caso seja de tipo certo.

```php
use App\\Exceptions\\InvalidOrderException;
 
/**
 * Register the exception handling callbacks for the application.
 */
public function register(): void
{
    $this->reportable(function (InvalidOrderException $e) {
        // ...
    });
}
```

```php
$this->reportable(function (InvalidOrderException $e) {
    // ...
})->stop();
 
$this->reportable(function (InvalidOrderException $e) {
    return false;
});
```

Quando registamos uma excessão customizada usando o metodo reportable, o Laravel vai loggar a excessão com a configuração default para a aplicaçao.

Se quiseres parar a propagação da excessão, podes usar o metodo `stop` ou fazer return `false`.

```php
/**
 * Get the default context variables for logging.
 *
 * @return array<string, mixed>
 */
protected function context(): array
{
    return array_merge(parent::context(), [
        'foo' => 'bar',
    ]);
}
```

```php
<?php
 
namespace App\\Exceptions;
 
use Exception;
 
class InvalidOrderException extends Exception
{
    // ...
 
    /**
     * Get the exception's context information.
     *
     * @return array<string, mixed>
     */
    public function context(): array
    {
        return ['order_id' => $this->orderId];
    }
}
```

Quando possivel, o Laravel vai guardar algumas variaveis globais como o `User’s ID` na exception message.

Se precisares de mais variaveis de contexto podes declara-las ao criar o metodo `context()` na class **`App\\Exceptions\\Handler`.**

Se precisares variaveis globais mais especificas para certos tipos de excessão podes declarar o metodo `context()`.