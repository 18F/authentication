---
permalink: /oauth/
title: Oauth
---
Oauth relies on authentication tokens that identify a resource owner (human,
organization, or application) and grant the receiving application access to
various components of the owner's identity for further
[authorization]({{ site.baseurl }}/authentication-vs-authorization/), without
exposing the owner's credentials.

There are two flavors: the original OAuth as described in [RFC
5849](http://tools.ietf.org/html/rfc5849) and the more recent OAuth 2.0 from
[RFC 6749](http://tools.ietf.org/html/rfc6749). OAuth2.0 is significantly more
complex, but is also becoming more widely implemented by major identity
providers.

The basic flow is:

- An as-yet-unauthenticated client makes a request for a protected resource.
- If the client is not logged into the OAuth provider, the server redirects
  the client to the provider to log in.
- Once the client is logged in, the client grants the server's application
  access to various component's of the client's identity, if access has not
  yet been granted.
- The OAuth provider redirects the client back to the application server with
  authentication credentials.
- The server either grants or denies access to the requested resource based on
  the provider-supplied credentials.

## Advantages

Identity resources are managed in one place, by the OAuth provider.

Permissions may be granted to individual applications without sharing
passwords and other user information.

Permissions may be revoked for specific applications.

## Drawbacks

The OAuth protocol is complex, and must be integrated directly into an
application rather than allowing a web server to configure it. This can be
mitigated using a tool such as the
[oauth2_proxy]({{ site.baseurl }}/oauth/oauth2_proxy/) that handles the OAuth
flow and forwards the credentials to the receiving application.

There is no validation of the integrity of the request.
