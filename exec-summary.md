# PDS Interop: Solid-Nextcloud

This project connects the world of Solid with the world of Nextcloud.
The aim is to develop an open source Nextcloud app that turns a Nextcloud
server into a spec-compliant Solid server. It gives every user a WebID profile
and allows Solid apps to store data on the user's Nextcloud account.

It also exposes some of the user's existing Nextcloud data like contacts and
calendar events as Solid user data, so that Solid apps can interact with the user's
Nextcloud data, and allow the user to manage which Solid apps can access which
specific aspects of the user's personal data.

We will make our implementation compatible with the latest version of the Solid spec
(including DPop tokens and the WebSockets AUTH command), and contribute the surface
tests we create for this as a well-documented independent test-suite, for other Solid
server implementers to benefit from.

We will also publish a stand-alone version of our PHP components, which can run independently of Nextcloud.
