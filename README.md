# google-sheets-api-php-client

PHP client library for Google Sheets API.

## Requirements

- PHP 5.6+

## Installations

```bash
$ composer require ttskch/google-sheets-api-php-client:@dev
```

## Usage

```php
// create \Google_Client instance with your OAuth2 client ID.
$googleClient = \Ttskch\GoogleSheetsApi\Factory\GoogleClientFactory::create(
    'client_id',
    'client_secret',
    'redirect_uri',
    'javascript_origin'
);

// authenticate and be athorized.
$authenticator = new \Ttskch\GoogleSheetsApi\Authenticator($googleClient);
if (isset($_GET['code'])) {
    $authenticator->authenticate($_GET['code']);
} else {
    $authenticator->authorize();
}

// create API client with authorized Google_Client.
$api = \Ttskch\GoogleSheetsApi\Factory\ApiClientFactory::create($googleClient);

$service = $api->getGoogleService();

// now you can call all apis via $service.
// see \Google_Service_Sheets class to learn more about details.
$service->spreadsheets->...;
$service->spreadsheets_sheets->...;
$service->spreadsheets_values->...;
```

See also [demo](demo).
