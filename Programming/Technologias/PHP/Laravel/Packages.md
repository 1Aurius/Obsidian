## Packages

que es eso?

## >**Exemplo** prático

instalar o Pacote “breeze”…

### 1) Criamos o require no composer.json do projeto

### **`composer require laravel/breeze --dev`**

### Composer.json

```json
"require-dev": {
        "fakerphp/faker": "^1.9.1",
        **"laravel/breeze": "^1.19"**,
        "laravel/pint": "^1.0",
        "laravel/sail": "^1.0.1",
        "mockery/mockery": "^1.4.4",
        "nunomaduro/collision": "^6.1",
        "phpunit/phpunit": "^9.5.10",
        "spatie/laravel-ignition": "^1.0"
    },
```

### 2) Correr o comando `**breeze**:install`

### ````````````**php artisan** **breeze**:install`

### A resposta das seguintes questões:

**0 | y | n**

## DONE! Agora, na pagina `**welcome**.blade.php` deve ter os botões de **Log in** e **Register**

---

### Mas espera, se temos breeze, que por si tem um sistema de log in e sign in, como é que vamos ter acesso mysqli ou uma base de dados em geral???

Check out this dope page :)

## Introdução

No Laravel, um pacote é uma extensão ou conjunto de funcionalidades que se pode adicionar a um projeto.

Estes pacotes são desenvolvidos por diferentes pessoas ou empresas e furnecem recursos pre-feitos para o teu projeto.

Pensa em pactoes como conjuntos de ferramentas cheios de funcionalides para o teu projeto.

## Como adicionar Packages ao teu projeto?

Se quiseres adicionar um pacote a um projeto que tenhas precias do composer e do **composer**.**json** do projeto.

O comando:

`**php composer.phar require laravel/<nome do pacote> --dev`**

<aside> 📑 **!!ATENÇÃO!!** Se o teu composer.phar não estiver defenido como enviroment variable, teras de navegar para encontrar o ficheiro. `**php ../composer.phar require laravel/<nome do pacote> --dev**`

</aside>

Depois de termos algo como :

```json
"require-dev": {
        "laravel/nomeDoPacote": "versão",

```

Podemos correr o comando:

**`php artisan nomeDoPacote:install`**