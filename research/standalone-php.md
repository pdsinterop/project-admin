# Standalone PHP Solid Server

This document outlines what is to be build for the standalone version of the PHP Solid server. Details and references to specifications are also added.

## Goals

0. Empty Server
1. Identity<br>
   a. WebID provider<br>
   b. WebID authentication module
2. Solid storage API
3. Web ACL

## 0. Server

- All http URIs MUST redirect to their https counterparts using a response with a 301 status code and a Location header.

- It SHOULD additionally implement the server part of HTTP/1.1 Caching to improve performance

- When a client does not provide valid credentials when requesting a resource that requires it, the data pod MUST send a response with a 401 status code (unless 404 is preferred for security reasons).

- A Solid server MUST reject PUT, POST and PATCH requests without the Content-Type header with a status code of 400.

- Paths ending with a slash denote a container resource. the server MAY respond to requests for the latter URI with a 301 redirect to the former.

## 1. Identity

### a. WebID Profile Document

Defined by the [**Solid WebID Profiles Spec**][1]:

- MUST have a `foaf:primaryTopic` predicate
- MUST have a primary topic be a valid `foaf:Agent` type, such as `foaf:Person`
- MUST identify the document as a `foaf:PersonalProfileDocument` instance
- MUST include a `foaf:name` MAY be a pseudonym
- MUST support separate public and private data in a user's profile.
- SHOULD include `cert:key` public key certificate (for use with WebID+TLS)
- SHOULD include a public avatar `foaf:img`
- SHOULD link to Solid Storage container(s) using `pim:storage` (for applications data read/write).
- SHOULD link to Type Registry Index resources
  - _If these links exist there MUST be only one link each to a private and a public type registry index file_
- MAY provide a `foaf:nick` nickname
- MAY contain a link to the Solid Inbox container using `ldp:inbox`
  - _If an inbox link exists it MUST be only one Inbox for the profile_
- MAY be split into multiple RDF resources linked together (via `owl:sameAs`, `rdfs:seeAlso`, or `space:preferencesFile`)

Inherited from the [**WebID spec**][2]:

- MUST be available as `text/turtle`<br>
- MUST have a HTTP URI that dereferences to a document the user controls
- MAY be available as othe RDF formats if requested through content negotiation

#### Example URLs:

- `/{user}/profile` (public profile)
- `/{user}/preferences` (private preferences profile)

[1]: https://github.com/solid/solid-spec/blob/master/solid-webid-profiles.md
[2]: https://www.w3.org/2005/Incubator/webid/spec/identity/

### b. WebID authentication module

> A Solid data pod MUST conform to the WebID-OIDC specification
> A Solid data pod MAY conform to the WebID-TLS specification

- WebID-TLS
- WebID-OIDC

## 2. Solid storage API

- HTTP verbs
- RDF-aware parts
- sparql-update
- content-negotiation

## 3. Web ACL

> A Solid data pod MUST conform to the Web Access Control specification

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

## Related projects and other resources

- https://github.com/semsol/arc2 -  ARC RDF Classes for PHP
  > ARC2 is a PHP 7.2 library for working with RDF. It also provides a MySQL-based triplestore with SPARQL support. Older versions of PHP may work, but are not longer tested.

- https://github.com/cgutteridge/Graphite - PHP RDF Library
  > Graphite is a friendly API for working with graph data (RDF).

- https://github.com/melvincarvalho/libAuthentication - authentication for the web
  > libAuthentication is a PHP implementation of the FOAF+SSL [WebID+TLS] protocol.


- https://github.com/easyrdf/easyrdf - library to consume and produce RDF.
  > EasyRdf is a PHP library designed to make it easy to consume and produce RDF.

- https://github.com/lanthaler/JsonLD -  JSON-LD processor for PHP
  > JsonLD is a fully conforming JSON-LD processor written in PHP. It is extensively tested and passes the official JSON-LD test suite.

- https://github.com/dajobe/raptor Redland Raptor RDF syntax library
  >

- "Indicating, Discovering, Negotiating, and Writing Profiled Representations"
  https://profilenegotiation.github.io/I-D-Profile-Negotiation/I-D-Profile-Negotiation.html
  > A Solid data pod MAY conform to the Profile-based Content Negotiation specification
