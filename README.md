# BeSimpleSoapClient

The BeSimpleSoapClient is a component that extends the native PHP SoapClient with further features like SwA, MTOM and WS-Security.

# For Orange/EE M2M users

## Installation:
Add `"robcaw/soap-client": "0.2.*@dev"` to your `composer.json` and run `composer update`.

Do some SOAP client:

```
use BeSimple\SoapClient\SoapClient as Soap;

$options = array(
    "trace"=> true,
    "exceptions"=> false, //Exceptions must be false for this workaround.
    'curl_ssl_version' => 3, //Must be version 3 for Orange/EE wsdl
);

$soap = new Soap($url, $options);

//The next line alone doesn't work, as the SoapClient doesn't think the response is XML
$soap->peekMessages($username, $password, 50);

//So it must be followed up by
$xml = $soap->__getLastResponse();

```
