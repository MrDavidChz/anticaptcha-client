anticaptcha-client
==================
Powerful and easy [anti-captcha.com](http://getcaptchasolution.com/djbj8qnktb) API wrapper.

[![Build Status](https://scrutinizer-ci.com/g/gladyshev/anticaptcha-client/badges/build.png?b=master)](https://scrutinizer-ci.com/g/gladyshev/anticaptcha-client/build-status/master)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/gladyshev/anticaptcha-client/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/gladyshev/anticaptcha-client/?branch=master)

### Install 

```bash
$ composer require gladyshev/anticaptcha-client
```
or 
```php
"require": {
  ...
  "gladyshev/anticaptcha-client": "*"
  ...
}
```

### Examples
More examples in [examples](/examples) folder.

```php
$client = new \Anticaptcha\Client('YOUR_API_KEY', ['languagePool' => 'en']));

$taskId = $client->createTaskByImage(__DIR__.'/data/yandex.gif');
$result = $client->getTaskResult($taskId);
$result->await(); // Waiting for completion of solution.

var_dump($result->getSolution()->getText()); // string(14) "замочка"
```

### Client options

Option | Type | Default | Description 
---| --- | --- | ---
`language` | string | null | Error messages language (null - English). Available are 'en_US' and 'ru_RU'.
`languagePool`| string | 'rn' | Sets workers pool language. At the moment the following language pools are available: en (default) : English language queue rn : group of countries: Russia, Ukraine, Belarus, Kazahstan.
`serverUrl`| string	| 'https://api.anti-captcha.com' | Anti-captcha API URL.
`transport` | \GuzzleHttp\ClientInterface | — | Guzzle library HTTP client, set you own configured client for debug issues or logging for example. 
`credentials` | \Anticaptcha\CredentialsInterface | — | Credentials object contains API key only.

The library strictly follows the API documentation, so full features can be found by looking at the [official documentation](https://anticaptcha.atlassian.net/wiki/spaces/API/pages/196635/Documentation+in+English) of the service.