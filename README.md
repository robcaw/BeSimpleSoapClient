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

# Features (only subsets of the linked specs implemented)

* SwA: SOAP Messages with Attachments [Spec](http://www.w3.org/TR/SOAP-attachments)
* MTOM: SOAP Message Transmission Optimization Mechanism [Spec](http://www.w3.org/TR/soap12-mtom/)
* WS-Security [Spec1](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf), [Spec2](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)
* WS-Adressing [Spec](http://www.w3.org/2002/ws/addr/)

# Installation

If you do not yet have composer, install it like this:

```sh
curl -s http://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin
```

Create a `composer.json` file:

```json
{
    "require": {
        "robcaw/soap-client": "0.2.*@dev"
    }
}
```

Now you are ready to install the library:

```sh
php /usr/local/bin/composer.phar install
```
