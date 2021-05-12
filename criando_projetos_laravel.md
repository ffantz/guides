# Criando projeto laravel:

- Criando projeto na versão 7 do Laravel:
```
    composer create-project --prefer-dist laravel/laravel:7.0 {nome_projeto}
    cd {nome_projeto}
    git init
```
- Adicionar no composer.json:
```
    # require:
        "laravel/framework": "^7.0",
        "laravel/horizon": "^4.3",
        "laravel/passport": "^9.3",
        "laravel/tinker": "^2.0",
        "predis/predis": "^1.1",
        "lucascudo/laravel-pt-br-localization": "dev-master",
        "mopo922/laravel-treats": "^2.0",
        "ramsey/uuid": "^4.1",
        "darkaonline/l5-swagger": "^8.0",
        "doctrine/dbal": "^2.9",
        "laravel/helpers": "^1.4",
        "laravel/ui": "^2.4"
    # autoload:
        "files": [
            "app/Helpers/helpers.php"
        ],
    # scripts:
        "definir-env-producao": [
            "php -r \"copy('.env.example.production', '.env');\"",
            "php artisan key:generate"
        ],
        "definir-env-dev": [
            "php -r \"copy('.env.example.dev', '.env');\"",
            "php artisan key:generate"
        ],
        "definir-env-test": [
            "php -r \"copy('.env.example.test', '.env');\"",
            "php artisan key:generate"
        ],
```
```
    composer install
```

- Definir as rotas e pastas do Auth:
```
    php artisan ui vue --auth
    npm install
    npm run dev
```

- Definir os dados no arquivo `env.example.dev`, tais como dados de banco e demais variáveis

```
    composer definir-env-dev
```
- Alterar o arquivo `logging.php` para utilizar o channel daily no stack

```
    'stack' => [
        'driver' => 'stack',
        'channels' => ['daily'],
        'ignore_exceptions' => false,
    ],
```
- Alterar o arquivo `mail.php` para utilizar o env `MAIL_DRIVER` no default

```
    'default' => env('MAIL_DRIVER', 'smtp')
```

- Alterar o arquivo `filesystem.php`:

```
    'default' => env('FILESYSTEM_DRIVER', 'public')
```

- Rodar as migrates

```
    php artisan migrate
```

- Anotar os dados retornados de secret e id
```
    php artisan passport:install --uuids
```

- Definir os clientes, criar um para cada sistema que irá consumir a api:
```
    php artisan passport:client
```

- Adicionar os middlewares no `Kernel.php`

```
    app/Http/Kernel.php
    'auth.apitoken' => \App\Http\Middleware\AuthenticateApiToken::class,
```

- Levar o gcrud, junto com seus templates

```
    app/Console/Kernel.php

    protected $commands = [
        Commands\CreateCRUD::class,
    ];

    resources/views/crud_templates
```

- Levar traits basicas, como scope e prepare trait
- Levar generic repository
- Levar repository interface
- Levar custom rules request
- Levar config httpstatus
- Levar baseModel
- Ajustar arquivo `AuthServiceProvider`, incluindo o passport
- Definir seeders, models

- Horizon:

```
    php artisan horizon:install
    php artisan horizon:publish
```

- Adicionar os modes no mysql em `database.php`

```
    'modes' => [
        'STRICT_TRANS_TABLES',
        'NO_ZERO_IN_DATE',
        'NO_ZERO_DATE',
        'ERROR_FOR_DIVISION_BY_ZERO',
        'NO_ENGINE_SUBSTITUTION',
    ],
```

- Adicionar o auth no redis em `database.php`

- Definir guards, quantos necessários (eles entram na validação de middleware) no `auth.php`

```
    'api' => [
        'driver' => 'passport',
        'provider' => 'users',
        'hash' => false,
    ],

    'apitoken' => [
        'driver' => 'token',
        'provider' => 'users',
        'hash' => false,
    ],

```

- Provider (`auth.php`):

```
    'providers' => [
        'users' => [
            'driver' => 'eloquent',
            'model' => App\Models\Usuario::class,
        ],
    ],
```

- Para utilizar um model como autenticador, importe as classes nele:

```
    use Illuminate\Foundation\Auth\User as Authenticatable;
    use Laravel\Passport\HasApiTokens;

    class Empresa extends Authenticatable
    {
        use HasApiTokens;
    }
```

- No `kernel.php`, especificar o arquivo de middleware

```
    'auth.apitoken' => \App\Http\Middleware\AuthenticateApiToken::class,
```
- [Instalando certificado digital no servidor](https://certbot.eff.org/lets-encrypt/ubuntubionic-nginx)

- PHP Redis:
```
    sudo apt-get install php7.3-dev
    sudo apt-get install php-redis
```