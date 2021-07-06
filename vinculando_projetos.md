# Vinculando projetos como sistema no Orquestrador:

- O vínculo de um novo projeto sempre ocorre no backend da aplicação. O tutorial a seguir presume que o back esteja em uma API Laravel.
---
### Configurando .env
- É necessário adicionar as informações de `client_id`, `client_secret` e host do redis no `.env`:

```
    ID_CLIENT_API_AUTH=""
    SECRET_API_AUTH=""
    REDIS_API_AUTH_HOST=""
```
- Para obter o `client_id` e `client_secret`, é necessário rodar o seguinte comando no `api_auth`:
```
    php artisan passport:client
```
- As informações geradas deverão ser salvas no .env
    - Para as informações do host em prod, consultar o `.env` do `api_motor_credito`

- Levar o arquivo `AuthSso.php`, do `api_motor_credito` para a mesma estrutura de pastas no projeto alvo.

- Em `app/Http/Kernel.php`, adicionar a segunte linha dentro do array `$routeMiddleware`:
```
    'auth.sso' => Middleware\AuthSso::class
```

- Por fim, nas rotas do `api.php`, definir o `middleware` no agrupamento das rotas:
```
    [
        'middleware' => ['auth.sso']
    ]
```