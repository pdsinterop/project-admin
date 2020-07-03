# PHP Libraries

This document outlines the various PHP libraries that could be of use to this
project, which ones were choosen, and why.

## Topics

If possible, libraries should be used for:

- Content negotiation
- CORS Header management
- Crypto / Certificates
- File converter (CSV / JSON / TSV / XML)
- HTTP Request/Response
- JSON Security (JOSE, JWA, JWE, JWK, JWS, JWT)
- OAuth2
- OpenID
- RDF (Turtle, JSON-LD, RDFa, ...)
- SPARQL
- Vocabulary (Dublin core, Schema.org, Owl, FoaF, ...)
- WebID
- WSS

<!--
- LDP Containers ?
 -->


## Requirements / Criteria

Besides being compatible with the license we use (MIT), there are several other
criteria a library must meet if we are to use it.

- Adhere to [IETF](https://tools.ietf.org/html/), [W3C](https://www.w3.org/TR/),
  and other relevant standards (for instance [Dublin Core](https://www.dublincore.org/specifications/) [OpenID](https://openid.net/developers/specs/))
- Adhere to [accepted PHP Standard recommendations](https://www.php-fig.org/psr/#accepted)
- Be a healthy open-source project.

As the world is not a perfect place, deviation from these criteria is possible.
In such a case, the reasoning as to _why_ to deviate will be documented

## Healthy open-source

Besides being open-source, in order to be healthy, a library also needs to:

- **Be actively maintained**
  So there is convidence the library will remain supported)

- **Be well documented**
  So the learning curve is less steep

- **Have somewhat of a community**
  So answers to questions are already out there

It would be helpful if projects adhere to current [FOSS best practices](https://bestpractices.coreinfrastructure.org/),
but not required.

### PHP Standard recommendations

There are several standard recommendations for PHP (PSR) that are relevant to
this project. They are:

- [PSR-7][PSR-7] for HTTP messages
- [PSR-11][PSR-11] for dependency injection container
- [PSR-15][PSR-15] for HTTP server middleware
- [PSR-17][PSR-17] for HTTP message factory
- [PSR-18][PSR-18] for HTTP client requests

[PSR-7]: https://www.php-fig.org/psr/psr-7/
[PSR-11]: https://www.php-fig.org/psr/psr-11/
[PSR-15]: https://www.php-fig.org/psr/psr-15/
[PSR-17]: https://www.php-fig.org/psr/psr-17/
[PSR-18]: https://www.php-fig.org/psr/psr-18/

Whenever a choice needs to be made, libraries that adhere to PSR have preference
over those that do not.

### Standards

Besides the PSR conventions, there are also various other standards that are of
importance.

Whenever a choice needs to be made, libraries that adhere to these have
preference over those that do not.

<!-- @TODO: Add link to standards from solid specs doc when it is done

How these standards relate to eachother can be seen in [the PDS Interop Solid specs overview](https://pdsinterop.org/solid-specs-overview/)
-->

## Libraries

The following libraries are available.

<!-- This section should look a bit like this:
### Topic

- Lbrary X - Short burb for Library X
- Library Y -Short text about why Library Y is awesome

Choosen: **Library X**

_Rationale behind choosing this library over others_
-->

<!-- ### Content negotiation -->

<!-- ### CORS Header management -->

### Crypto / Certificates

- [`defuse/php-encryption`](https://github.com/defuse/php-encryption)
  _"Simple Encryption in PHP."_
- [`jedisct1/libsodium-php`](https://github.com/jedisct1/libsodium-php) _"The PHP extension for [libsodium](https://github.com/jedisct1/libsodium)."_
- [`paragonie/sodium_compat`](https://github.com/paragonie/sodium_compat) _"Pure PHP polyfill for ext/sodium"_

<!-- ### File converter (CSV / JSON / TSV / XML) -->

### HTTP Request/Response

- [`laminas/laminas-diactoros`](https://github.com/laminas/laminas-diactoros) _"PSR HTTP Message implementations"_
- [`php-http/httplug`](https://github.com/php-http/httplug) _"HTTPlug, the HTTP client abstraction for PHP"_

### JSON Security (JOSE, JWA, JWE, JWK, JWS, JWT)

- [`firebase/php-jwt`](https://github.com/firebase/php-jwt) _"PHP package for JWT"_
- [`lcobucci/jwt`](https://github.com/lcobucci/jwt) _"A simple library to work with JSON Web Token and JSON Web Signature"_
- [`namshi/jose`](https://github.com/namshi/jose) _"JSON Object Signing and Encryption library for PHP."_
- [`web-token/jwt-framework`](https://github.com/web-token/jwt-framework) _"JWT Framework"_

### OAuth2

- [`league/oauth2-server`](https://github.com/thephpleague/oauth2-server) _"A spec compliant, secure by default PHP OAuth 2.0 Server"_

### OpenID

#### OpenID Connect (OIDC)

- [`bshaffer/oauth2-server-php`](https://github.com/bshaffer/oauth2-server-php) _"A library for implementing an OAuth2 Server in php"_
- [`jumbojett/openid-connect-php`](https://github.com/jumbojett/OpenID-Connect-PHP/) _"Minimalist OpenID Connect client"_
- [NextCloud OIDC Login](https://github.com/pulsejet/nextcloud-oidc-login) _"Nextcloud login via a single OpenID Connect 1.0 provider"_

### RDF (Turtle, JSON-LD, RDFa, ...)

- [Easyrdf](https://github.com/easyrdf/easyrdf) _"EasyRdf is a PHP library designed to make it easy to consume and produce RDF."_
- [`semsol/arc2`](https://github.com/semsol/arc2) _"ARC RDF Classes for PHP"_

<!-- ### SPARQL -->

<!-- ### Vocabulary (Dublin core, Schema.org, Owl, FoaF, ...) -->

<!-- ### WebID -->

<!-- ### WSS -->
