# Risks

What are critical points? Where can we hit a wall?

1. nextcloud oauth support
2. nextcloud acl support
3. solid specification stability
4. link nextcloud data to json-ld/triples
5. Apache 304 CORS support

## 1. nextcloud oauth support

There is an oauth2 app in the official distribution. It is marked as
incomplete though. It only grants full access to a users repository.

## 2. nextcloud acl support

We need to find out if nextcloud supports something that we link to solid's
acl standard.


## 3. solid specification stability

We need to find out if the solid spec is stable enough to work with.

## 4. link nextcloud data to json-ld/triples

We need to find out if there are rdf/linked data vocabularies for the most
common datasets in nextcloud. We need to select which datasets we want to
support.

## 5. Apache 304 CORS support
In the past, Apache produced its own 304 responses without going through PHP,
making it impossible for the code to produce the desired CORS headers. I *think* this was recently fixed in Apache.
