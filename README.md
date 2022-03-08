# mailer-notes
Notes for configuration of PHPMailer


https://oit.ncsu.edu/campus-it/email/about/

## Some install notes

https://github.com/PHPMailer/PHPMailer/wiki/Using-Gmail-with-XOAUTH2

https://artisansweb.net/how-to-send-email-using-gmail-api-with-phpmailer/

## Link to get_oauth_token.php on localhost

http://localhost/tbas2_3/ext/PHPMailer/get_oauth_token.php

## Login here to configure.

To edit search gmail api

https://console.cloud.google.com/cloud-resource-manager

This is the oauth library.
Use this to update outdated code in get_oauth_token.php

https://oauth2-client.thephpleague.com/providers/league/

```
sudo apt install composer
composer require league/oauth2-google
```
Go here to create keys.
https://console.developers.google.com/

1. create credentials
2. OAuth client ID
3. Web Application
4. add Authorized redirect URIs - http://localhost/tbas2_3/ext/PHPMailer/get_oauth_token.php
5. create
6. download json
7. open oauth2-google and set $clientId and $clientSecret from the json or the google api page.
8. set the $redirectUri for server retrieving the token, eg http://localhost/phpmailer/get_oauth_token.php
9. Adust path to autoload.php according to where it is intsalled and update methods from the oauth2-client.thephpleague.com example

```
require '../vendor/autoload.php';

$authUrl = $provider->getAuthorizationUrl($options);
$_SESSION['oauth2state'] = $provider->Getstate();

 echo $token->getToken() . '<br><br>';

// Use this to get a new access token if the old one expires
echo $token->getRefreshToken() . '<br><br>';

// Unix timestamp at which the access token expires
echo $token->getExpires() . '<br>';

```

The script should now run and put the client id, secret and token printed from the script in the file copied from examples/gmail_xoauth.phps