# Milestones

All of these milestones are organized in 4 topics.
We will request payment of 5,000 euros for each milestone from the
[Next Generation Internet Privacy & Trust
Enhancing Technologies (NGI-Zero:PET) grant](https://nlnet.nl/PET/) for a total
of 50,000 euros.

The milestones are:

1. Identity
   - 1a. Test Suite (€5,000)
   - 1b. Standalone PHP server(€5,000)
   - 1c. Nextcloud Integration (€5,000)

2. Storage API
   - 2a. Test Suite (€5,000)
   - 2b. Implementation (€5,000)

3. Web ACL
   - 3a. Test Suite (€5,000)
   - 3b. Implementation (€5,000)

4. Deep Integration with Nextcloud
   - 4a. Solid App Launcher (€5,000)
   - 4b. Contacts and Profile (€5,000)
   - 4c. Calendar (€5,000)

Each milestone is described in more detail below.

## 1. Identity

The Solid identity protocol was changed in 2019 and is again being changed in
2020. A [test-suite](https://github.com/solid/test-suite) for the 2019 version
of webid-oidc was developed by [Inrupt](https://inrupt.com), but it was
incomplete and partially incorrect.

The official documentation for the 2020 version of the [WebID-OIDC](https://github.com/solid/webid-oidc-spec)
protocol using [DPop](https://tools.ietf.org/html/draft-fett-oauth-dpop-04) has
not yet been finalized, and ours will be among the first implementations of it,
along with [Node-Solid-Server]( https://github.com/solid/node-solid-server) and
[Solid-App-Kit](https://github.com/michielbdejong/solid-app-kit).

This means that in order to implement it in PHP, we need a reliable test-suite
first, that tests whether a given server is acting as a spec-compliant identity
provider.

### 1a. Test Suite

This milestone is for writing the parts of the test-suite that relate to:

- Correctness of the authorization endpoint
- Fetching the OpenID config
- Fetching the WebID profile
- Generating access tokens

The tests which will check compatibility between our implementation in PHP
(Nextcloud-based/stand-alone), Node, and Solid-App-Kit.

The exact test criteria this test suite tests for will be detailed on a
dedicated public web page on https://pdsinterop.org/, with links to the relevant
sections in the official Solid spec.

### 1b. Standalone PHP

This milestone will be for creating an empty standalone PHP server (that all
following standalone PHP milestones will be implemented in), an identity
(WebID profile), and a Solid identity provider in PHP.

Any generic parts will be implemented as package(s) that can be re-used by the
Nextcloud integration (and any future PHP implementations).

The implementation will pass all of the test in the test-suite from the
Identity Test Suite milestone (1a).

### 1c. Nextcloud Integration

This milestone will be for a Nextcloud app (that all following Nextcloud
milestones will be implemented in), a WebID profile, and integrate the Solid
identity provider into the Nextcloud app (using any packages created in the 
previous milestone).

The data in the profile will be based on user data from the Nextcloud database.

The identity provider will use Nextcloud's existing single  sign-on feature as
the user login database.

The implementation will pass all relevant tests from the Identity Test Suite
milestone.

## 2. Storage API

Part of this is already tested by the LDP-BasicContainer test-suite, but for
many details (such as filename encoding, recursive deletes, sparql-update and
race conditions), a reliable test suite is still needed.

This will to the benefit of both our project as well as future Solid server
implementation projects.

### 2a. Test Suite

This milestone will be for providing a test suite that tests the different
behaviours which the storage API of a Solid server needs to implement.

The exact test criteria this test suite tests for will be detailed on a
dedicated public web page on https://pdsinterop.org/, with links to the relevant
sections in the official Solid spec.

### 2b1. Standalone PHP

This milestone will implement the Solid storage API in standalone PHP, in such a
way that any generic parts can be re-used (as package) in the Nextcloud
integration.

It encompasses the various HTTP verbs, as well as RDF-aware parts like
sparql-update and content-negotiation.

The implementation will pass all relevant tests from the Storage API Test Suite
milestone.

### 2b2. Nextcloud Integration

This milestone will include the integration of the Solid storage API into the
Nextcloud app (using any packages created in the previous milestone).

The implementation will pass all relevant tests from the Storage API Test Suite
milestone.

## 3. Web ACL

The Web ACL protocol is quite complex and at times confusing. One description of
it is available at https://github.com/solid/web-access-control-spec, and a
slightly more readable and explicit interpretation of it is available at
https://unhosted.org/using-solid/.

A reference implementation is available in Node-Solid-Server and Solid-App-Kit,
however, no good test suite is available for it, so there would be no good way
to know if our implementation would be compatible.

**It is absolutely crucial for the security of private data that the Access
Control Lists are interpreted in exactly the same way by each implementation of
the Solid spec, including our Nextcloud-based one.**

### 3a. Test Suite

This milestone will provide a test suite that checks and ensures that our
implementation is both correct as intended, and compatible with other
implementations.

The exact test criteria this test-suite tests for will be detailed on a
dedicated public web page on https://pdsinterop.org/, with links to the relevant
sections in the official Solid spec.

### 3b1. Standalone PHP

This milestone will implement the Web Access Control spec in standalone PHP, in
such a way that any generic parts can be re-used (as package) in the Nextcloud
integration.

The implementation will pass all relevant tests from the Web ACL Test Suite
milestone.

### 3b2. Nextcloud Integration

This milestone will include the integration of the Web Access Control spec into
the Nextcloud app (using any packages created in the previous milestone).

The implementation will pass all relevant tests from the Web ACL Test Suite
milestone.

## 4. Deep Integration

### 4a. Solid App Launcher

A crucial part of Solid is allowing the user to control who gets access to which
part of their data. The basis for this was developed last year at Inrupt, called
the Solid App Launcher, which we need to update and integrate into the user
interface of both the stand-alone server and the Nextcloud integration app.

The index of apps this launcher recognizes (and exact permissions each app
requests) will be detailed on a dedicated public web page on https://pdsinterop.org/,
with links to the relevant sections in the official Solid spec.

This milestone will implement the Solid App Launcher in the Nextcloud app.

### 4b. Contacts and Profile

Nextcloud users already have profile data like full name and avatar in their
user account, and they also already have a Nextcloud addressbook in which they
keep track of their contacts, for instance for sharing Nextcloud documents.

For this milestone we will unlock this data and make it available in the
RDF-based Solid data format for profile and contacts data.

The details of both the Solid and the Nextcloud data format for this will be
detailed on a dedicated public web page on https://pdsinterop.org/, with links
to the relevant sections in the official Solid spec.

This milestone will implement Contacts and Profile in the Nextcloud app.
This is an addition to the WebID profile from the "Identity Nextcloud 
Integration" milestone (1c).

### 4c. Calendar

Same as with Contacts and Profile but unlocking the user's Nextcloud-native
calendar events as Solid-native calendar events.

Where certain fields don't have a mapping (e.g. if the Solid format has a
maximum number of attendees for an event, but the Nextcloud format does not),
they will simply be left blank. Other than that, it will be a great way to
bootstrap the Solid app eco-system, where the millions of existing Nextcloud
users can instantly use Solid apps with their existing data.

The details of both the Solid and the Nextcloud data format for this will be
detailed on a dedicated public web page on https://pdsinterop.org/, with links
to the relevant sections in the official Solid spec.

This milestone will implement Calendar in the Nextcloud app.
