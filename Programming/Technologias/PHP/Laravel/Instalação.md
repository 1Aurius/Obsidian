## Como é que vamos instalar o Laravel?

---

- vamos utilizar uma ferramenta do php chamada “composer” e caso não a tenha instalado, tem aqui o link para o fazer.([LINK](https://getcomposer.org/download/))
- Agora que já temos ambos o Composer e o NodeJs, podemos realmente fazer a instalação do laravel a partir dos comandos nesta pagina([LINK](https://laravel.com/docs/10.x/installation))
- A versão que vamos utilizar é a 10x por isso garante que o installation guide está nessa mesma.

---

## TROUBLESHOOTING

- Eu instalei o nodejs mas não foi reconhecido, e agora?**(windows)**
    
    Tenta reiniciar o cmd, caso isso não funcione, renicia o computador em si.([LINK](https://stackoverflow.com/questions/10129505/node-not-recognized-although-successfully-installed))
    

## Important stuff

---

### hosting

O pacote Laravel já vem com um sistema de hosting do projeto e é ativado quando utilizamos este comando :

```json
php artisan serve
```

ATENÇÃO: Este comando tem de ser executado na diretoria do projeto ou não funciona;

Assim que o hosting começa, recebemos um link e podemos ver a nossa pagina :)

---

## Quando a Instalação estiver completa…

Podemos agora criar um projeto novo com o seguinte comando:

```json
composer create-project laravel/laravel example-app
```

(Muda o nome example-app com o nome do seu projeto)