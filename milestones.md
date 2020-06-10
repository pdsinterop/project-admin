# 1. Identity
## 1a. Test Suite
The Solid identity protocol was changed in 2019 and is again being changed
in 2020. A partial test-suite for the 2019 version was developed by Inrupt,
but it was incomplete and partially incorrect. The official documentation for the 2020
version of the WebID-OIDC protocol using DPop has not yet been finalized, and
ours will be among the first implementations of it, along with Node-Solid-Server and
Solid-App-Kit. This means that in order to implement it in PHP, we need a reliable
test-suite first, that tests whether a given server is acting as a spec-compliant
identity provider. This milestone is for writing this test-suite, which will check
compatibility between our implementation in PHP (Nextcloud-based/stand-alone),
Node-Solid-Server, and Solid-App-Kit. The exact test criteria this test suite tests for
will be detailed on a dedicated public web page on https://psdinterop.org/, with links
to the relevant sections in the official Solid spec.

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
implementation projects to benefit from. The exact test criteria this test suite tests for
will be detailed on a dedicated public web page on https://psdinterop.org/, with links
to the relevant sections in the official Solid spec.

## 2b. Implementation
This milestone will include both the implementation of the Solid storage API in PHP, and the integration
of that component into the Nextcloud app which was created in milestone 1c. It encompasses the various
HTTP verbs, as well as RDF-aware parts like sparql-update and content-negotiation.

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
The exact test criteria this test-suite tests for will be detailed on a dedicated public web page on
https://psdinterop.org/, with links to the relevant sections in the official Solid spec.

## 3b. Implementation
This milestone will include both the implementation of the Web Access Control spec in PHP, and the integration
of that component into the Nextcloud app which was created in milestone 1c.

# 4. Deep Integration
## 4a. Solid App Launcher
A crucial part of Solid is allowing the user to control who gets access to which part of their data. The basis
for this was developed last year at Inrupt, called the Solid App Launcher, which we need to update and integrate
into the user interface of both the stand-alone server and the Nextcloud integration app.
The index of apps this launcher recognizes, and exact permissions each app requests
will be detailed on a dedicated public web page on https://psdinterop.org/, with links
to the relevant sections in the official Solid spec.

## 4b. Contacts and Profile
Nextcloud users already have profile data like full name and avatar in their user account, and they also already
have a Nextcloud addressbook in which they keep track of their contacts, for instance for sharing Nextcloud documents.
For this milestone we will unlock this data and make it available in the RDF-based Solid data format for profile and
contacts data.
The details of both the Solid and the Nextcloud data format for this will be detailed on a dedicated public web page
on https://psdinterop.org/, with links to the relevant sections in the official Solid spec.

## 4c. Calendar
Same as 4b. but unlocking the user's Nextcloud-native calendar events as Solid-native calendar events. Where certain
fields don't have a mapping (e.g. if the Solid format has a maximum number of attendees for an event, but the Nextcloud
format does not), they will simply be left blank. Other than that, it will be a great way to bootstrap the Solid app
eco-system, where the millions of existing Nextcloud users can instantly use Solid apps with their existing data.
The details of both the Solid and the Nextcloud data format for this will be detailed on a dedicated public web page
on https://psdinterop.org/, with links to the relevant sections in the official Solid spec.
