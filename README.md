# Integração da API do Basecamp 3 com o Laravel 5

Esta **Integração da API do Basecamp 3 com o Laravel 5** proporcionará a integração da [nova API do Basecamp 3, atraves da 37 Signals][basecamp] com a [aplicação em Laravel 5][laravel].

## Instalação
Nós recomendamos utilizar o composer: (após a instalação do Laravel 5):

    $ php composer.phar require cgmalaquias/basecamp3-laravel

## Utilização

Para utilizar a biblioteca, será necessário ter uma conta criada no [https://integrate.37signals.com/][37signals]
Utilize a biblioteca do [Laravel Socialite][socialite]

### Authorization with username and password

```php
<?php

$client = \Basecamp\BasecampClient::factory(array(
    'auth' => 'http',
    'username' => 'you@email.com',
    'password' => 'secret',
    'user_id' => 99999999,
    'app_name' => 'My Wicked Application',
    'app_contact' => 'http://mywickedapplication.com'
));
```

### Authorization with OAuth token

This library doesn't handle the OAuth authorization process for you. There are already a lot of libraries out there which handle this process perfectly for you. When you recieved your token you'll have to pass it on to the client:

```php
<?php

$client = \Basecamp\BasecampClient::factory(array(
    'auth'     => 'oauth',
    'token'    => 'Wtj4htewhtuewhuoitewh',
    'user_id'   => 99999999,
    'app_name' => 'My Wicked Application',
    'app_contact' => 'http://mywickedapplication.com'
));

```
The following service operations are not (yet) covered by unit tests:

* updateTodo 
* grantAccess 
* updateCalendar 
* deleteCalendar 
* updateCalendarEvent 
* deleteCalendarEvent 
* updateProjectCalendarEvent 
* deleteProjectCalendarEvent 

<!--- END API -->

[basecamp]: https://github.com/basecamp/bc3-api
[laravel]: https://laravel.com/docs/5.3
[37signals]: https://integrate.37signals.com/
[socialite]: https://github.com/laravel/socialite
[guzzle]: http://guzzlephp.org/
[caching]: http://guzzlephp.org/plugins/cache-plugin.html
[service.php]: https://github.com/cgmalaquias/basecamp3-laravel/blob/master/src/Basecamp/Resources/service.php
