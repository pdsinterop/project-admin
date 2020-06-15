# solid-nextcloud

Goals (in order): 
1. use nextcloud as an identity provider for solid apps
2. use nextcloud file storeage as a data pod for solid apps
3. turn existing nextcloud app data (contacts, calendar, etc.) into linked data and provide these in data pods

## 1. Nextcloud as identity provider
Solid uses a new standard called WebID-OIDC (OIDC means OpenID Connect). This is a slight modification of the default OpenID Connect. OIDC itself uses OAuth2.
Nextcloud supports OAuth2 as an [OAuth2 Identity Provider](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/oauth2.html) out of the box. However, you can only grant full access to the users repository using this route. This is something which needs more work in nextcloud.
There doesn't seem to be much activity in the nextcloud community around this or OpenID. But here are two relevant pages where people are using this feature:

- [Nextcloud OAuth2 and Gitlab](https://www.claudiuscoenen.de/2018/10/oauth2-with-nextcloud-provider-and-gitlab-client/)
- [Nextcloud OAuth2 and Moodle](https://docs.moodle.org/36/en/OAuth_2_Nextcloud_service)

The relevant code is in the apps/oauth2 folder: [https://github.com/nextcloud/server/tree/master/apps/oauth2](https://github.com/nextcloud/server/tree/master/apps/oauth2)