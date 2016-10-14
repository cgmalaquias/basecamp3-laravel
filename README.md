# Integração da API do Basecamp 3 com o Laravel 5

The **Basecamp SDK for PHP** enables PHP developers to easily integrate [37signals Basecamp all new API][basecamp] into their applications.

**NOTE**: This library is under heavy development and a lot of calls haven't been implemented yet. We're looking forward to any of your PR's.

## Installation
We recommend Composer for managing dependencies. Installing is as easy as:

    $ php composer.phar require netvlies/basecamp-php

## Usage

To use the library the only requirement is you have a account.
Upon creating the client you have to pass your credentials or an OAuth token. Furthermore you need your userId to construct the URI's.

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

<!--- END API -->

[basecamp]: https://github.com/basecamp/bc3-api
[guzzle]: http://guzzlephp.org/
[caching]: http://guzzlephp.org/plugins/cache-plugin.html
[service.php]: https://github.com/cgmalaquias/basecamp3-laravel/blob/master/src/Basecamp/Resources/service.php
