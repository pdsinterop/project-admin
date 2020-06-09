# 1. Identity
## 1a. Test Suite
The Solid identity protocol was changed in 2019 and is again being changed
in 2020. A partial test-suite for the 2019 version was developed by Inrupt,
but it was incorrect and incomplete. The official documentation for the 2020
version of the WebID-OIDC protocol using DPop has not yet been finalized, and
ours will be the first implementation of it, but Node-Solid-Server and
Solid-App-Kit are expected to implement it soon as well. This means that in order to
implement it in PHP, we need a reliable test-suite first, that tests whether
a given server is acting as a spec-compliant identity provider. This milestone
is for writing this test-suite, which will check compatibility between our
implementation in PHP (Nextcloud-based/stand-alone), Node-Solid-Server, and Solid-App-Kit.

## 1b. Standalone
This milestone will be for implementing a Solid identity provider in PHP,
that passes the test-suite from the previous milestone.

## 1c. Nextcloud Integration
This milestone will be for integrating the Solid identity provider from the previous
milestone into Nextcloud, as a Nextcloud app, in such a way that Nextcloud's existing
single sign-on feature will be used as the user login database.

# 2. Storage API
## 2a. Test Suite
This milestone will be for providing a test suite that tests the different behaviours which
the storage API of a Solid server needs to implement. Part of this is already tested by the LDP-BasicContainer
test-suite, but for many details such as filename encoding, recursive deletes, sparql-update
and race conditions, a reliable test suite is still needed, both for our project and for other Solid server
implementation projects to benefit from.

## 2b. Implementation
This milestone will include both the implementation of the Solid storage API in PHP, and the integration
of that component into the Nextcloud app which was created in milestone 1c. It encompasses the various
HTTP verbs, as well as RDF-aware sparql-update and content-negotiation.

# 3. Web ACL
## 3a. Test Suite
The Web ACL protocol is quite complex and at times confusing. One description of it
is available at https://github.com/solid/web-access-control-spec, and a slightly more
readable and explicit interpretation of it is available at https://unhosted.org/using-solid/.
A reference implementation is available in Node-Solid-Server and Solid-App-Kit, however,
no good test suite is available for it, so there would be no good way to know if our implementation
would be compatible. It is absolutely crucial for the security of private data that the Access
Control Lists are interpreted in exactly the same way by each implementation of the Solid spec,
including our Nextcloud-based one. This milestone will provide a test suite that checks and
ensures that our implementation is both correct as intended, and compatible with other implementations.

## 3b. Implementation
This milestone will include both the implementation of the Web Access Control spec in PHP, and the integration
of that component into the Nextcloud app which was created in milestone 1c.

# 4. Deep Integration
## 4a. Solid App Launcher
## 4b. Contacts
## 4c. Calendar
