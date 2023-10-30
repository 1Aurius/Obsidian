## CROSS-SITE REQUEST FORGERIES

iso é um tipo de exploit feito por utilizadores autenticados quando estes correm comandos não autorizados.

Para nos proteger-mos deste exploit usamos o csrf_token.

### Pode ser usado de varias maneiras

```php
@Csrf
```

Dentro do form podemos colocar @Csrf e este vai acompanhar o submit do form.

```php
<input type="hidden" name="_token" value="{{csrf_token()}}"/>
```

O conceito é o mesmo mas o valor vai como hidden.

Sempre que quiseres passar o csrf token como hidden o nome default deve ser _token.

Quando fazemos submit de um form, este passa pelo [middleware](https://www.notion.so/Middleware-6c5d83644bb24dd2a95b7ae2746a538c?pvs=21) **VerifyCsrfToken**.