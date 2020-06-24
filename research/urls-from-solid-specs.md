# Available URLs in a SoLiD Server (a.k.a. POD or pod)

[![](https://img.shields.io/badge/project-Solid-7C4DFF.svg?style=flat-square)](https://github.com/solid/solid)

Reading trough the Solid specifications, the following URLs can be encountered:

```
/
/.acl
/2014/
/2014/financials
/2014/financials.acl
/2015/05/01/event1
/avatar.png
/card
/card#me
/data/
/data/*
/data/.acl
/data/.meta
/data/?query=SELECT%20*%20WHERE%20%7B%20%3Fs%20%3Fp%20%3Fo%20.%20%7D
/data/foo
/data/image.jpg
/data/image.jpg.meta
/data/res*
/data/res1
/data/res2
/data/test
/docs/
/docs/.acl
/docs/.acl/file1.acl
/docs/file1
/docs/file1.acl
/docs/shared-file1
/docs/shared-file1.acl
/documents/papers/.acl
/documents/papers/paper1
/documents/papers/paper1.acl
/inbox/
/notes/
/notes/social-web-2015
/notification/ping
/picture.jpg
/pingInbox/
/pingInbox/ping20.wac
/posts/1
/profile/
/profile/card
/profile/card#me
/settings/
/settings/preference
/settings/preferences
/work-groups#Accounting
/work-groups#Management
```

The sources where these URLs come from are listed below.

## Server Implementations

From [Recommendations for Server Implementations][1]

Data Containers

```
    /
    /inbox/
    /profile/
    /profile/card#me
    /settings/
    /settings/preference
```

[1]: https://github.com/solid/solid-spec/blob/HEAD/recommendations-server.md

## Content Representation

From: [Solid Content Representation Spec][2]

Objects and Metadata

```
    /posts/1
    /avatar.png

    /data/
    /data/.acl
    /data/.meta
    /data/image.jpg
    /data/image.jpg.meta
```

[2]: https://github.com/solid/solid-spec/blob/HEAD/content-representation.md


## WebID Profiles

From: [Solid WebID Profiles Spec][8]

```
    /profile/card
    /profile/card#me
    /settings/preferences
```

[8]: https://github.com/solid/solid-spec/blob/HEAD/solid-webid-profiles.md

## REST API

From the [Solid HTTPS REST API Spec][3]

```
    /data/*
    /data/res*
    /data/res1
    /data/res2

    /data/?query=SELECT%20*%20WHERE%20%7B%20%3Fs%20%3Fp%20%3Fo%20.%20%7D


    /picture.jpg
    /2015/05/01/event1
```

[3]: https://github.com/solid/solid-spec/blob/HEAD/api-rest.md

## WebSockets API

From: [Solid WebSockets API Spec][7]

```
    wss://example.org
    /data/
    /data/foo
    /data/test
```
[7]: https://github.com/solid/solid-spec/blob/HEAD/api-websockets.md

## User Stories

From: [UserStories / PrivateSharing][4]

```
    /card#me
    /2014/
    /2014/financials
    /2014/financials.acl
    /notification/ping
    /pingInbox/
    /pingInbox/ping20.wac
    pingInbox/ping20
```
[4]: https://github.com/solid/solid-spec/blob/HEAD/UserStories/PrivateSharing.md

From: [UserStories / User Profile Management][5]

```
    /card
```
[5]: https://github.com/solid/solid-spec/blob/HEAD/UserStories/UserProfileManagement.md

## Examples

From [User Posts a Note][6]

```
    /notes/
    /notes/social-web-2015
```

[6]: https://github.com/solid/solid-spec/blob/HEAD/examples/user-posts-note.md


## Web Access Control

From: [Web Access Control (WAC) Spec][9]

```
    /docs/
    /docs/.acl
    /docs/.acl/file1.acl
    /docs/file1
    /docs/file1.acl
    /docs/shared-file1
    /docs/shared-file1.acl
    /documents/papers/paper1
    /documents/papers/paper1.acl
    /documents/papers/.acl
    /.acl
    /profile/card#me

    /work-groups#Accounting
    /work-groups#Management

```
[9]: https://github.com/solid/web-access-control-spec/
