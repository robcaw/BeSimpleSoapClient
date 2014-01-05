# BeSimpleSoapClient

Forked from [BeSimple / BeSimpleSoapClient](https://github.com/BeSimple/BeSimpleSoapClient) to help fellow students on Secure Web Application Development overcome SoapClient issues with the EE M2M web service.

The BeSimpleSoapClient is a component that extends the native PHP SoapClient with further features like SwA, MTOM and WS-Security.

# For EE M2M users

## Installation:
Add `"robcaw/soap-client": "0.2.*@dev"` to your `composer.json` and run `composer update`.

Do some SOAP client:

```
use BeSimple\SoapClient\SoapClient as Soap;

$options = array(
    "trace"=> true,
    "exceptions"=> true,
    'curl_ssl_version' => 3, //Must be version 3 for Orange/EE wsdl
);

$soap = new Soap($url, $options);

$xml = $soap->peekMessages($username, $password, 50);

print_r($xml);
```

If you get a "Looks like we got no XML document" error, you can still get a response by adding `'exceptions' => false` to the options and running:

```
$xml = $soap->__getLastResponse();
```
