## Tinker

Tinker é uma shell para o nosso projeto laravel, ou seja, serve apenas para interagir com o nosso projeto

Para usar o Tinker, abrimos um terminal na diretoria do nosso projeto e escrevemos `php artisan tinker`.

## app()

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab41b57b-67bd-4d3b-a157-7fbc77842d5d/Untitled.png)

o comando dá nos varias informações sobre o nosso projeto.

---

Ao usar o exemplo ao lado ve-mos que podemos fazer get de todas as colunas da tabela User com o id 5.

Tambem podemos modificar rows da base de dados, exemplo:

```php
> $user->avatar= 'yippi';
= "yippi"

> $user->save()
= true
```

Ao fazer isto o valor avatar de User passa a ser ‘yippi’ e depois com o save() fica registado na própria base de dados.

### Tinker - PHP
o tinker é capaz de executar php.

---

Alternativamente podemos usar `→update([])`, que modifica e regista ao mesmo tempo. Mas devido á Mass Assignement temos que declarar o campo que queremos mudar no array $fillable do nosso modelo.