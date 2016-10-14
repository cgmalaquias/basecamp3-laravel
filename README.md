# Integração da API do Basecamp 3 com o Laravel 5

Esta **Integração da API do Basecamp 3 com o Laravel 5** proporcionará a integração da [nova API do Basecamp 3, atraves da 37 Signals][basecamp] com a [aplicação em Laravel 5][laravel].

## Instalação
Nós recomendamos utilizar o composer: (após a instalação do Laravel 5):

    $ php composer.phar require cgmalaquias/basecamp3-laravel

## Utilização

Para utilizar a biblioteca, será necessário ter uma conta criada no [https://integrate.37signals.com/][37signals]
Utilize a biblioteca do [Laravel Socialite][socialite]

Após a autenticação pelo Socialite, utilize a configuação abaixo em um controller chamado BasecampController.php, com 
### Utiize a autenticação via OAuth token

Abaixo um exemplo de como ficará seu controller com o handle e o callback:

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
use Socialite;
use Basecamp;

class BasecampController extends Controller {

    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function handle(Request $request) {
        return Socialite::driver('Thitysevensignals')->redirect();
    }

    public function callback(Request $request) {
        $user = Socialite::driver('Thitysevensignals')->stateless()->user();
        $client = Basecamp\BasecampClient::factory(array(
                    'base_url' => $user->user['accounts'][1]['href'],
                    'auth' => 'oauth',
                    'username' => $user->user['identity']['email_address'],
                    'user_id' => $user->user['identity']['id'], //$user->user['accounts'][1]['id'],
                    'app_name' => $user->user['accounts'][1]['name'],
                    'app_contact' => $user->user['identity']['email_address'],
                    'token' => $user->token
        ));
        //dd($user);
        dd($client);
    }

```
 No controller, você pdoerá criar os métodos, para aceitar todas as reuisições compostas nesta biblioteca, podendo fazer seus testes utitários:

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
