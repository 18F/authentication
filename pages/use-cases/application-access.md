---
permalink: /use-cases/application-access/
title: Authorizing user access to applications
parent: Use cases
---
This is a very familiar use case, whereby a human user logs into an
application and maintains a credential that permits access to part or all of
that application. This is the use case covered by the
[OAuth protocol]({{ site.baseurl }}/oauth/).

## Benefits

A user's credentials are managed by a single provider, and permissions may be
granted to multiple applications without sharing the user's password or other
information.

A user doesn't need to remember or enter multiple passwords for multiple
applications, provided every application has integrated a particular OAuth
provider.

The user can log out of the OAuth provider, and the OAuth token can eventually
expire, preventing unauthorized third parties from accessing systems using the
user's credentials should said party acquire a user's access token.

## Alternatives

The [basic HTTP authentication
scheme]({{ site.baseurl }}/basic-access-authentication/) may be used for
applications that don't need a high level of security, and may be configured
using standard web server settings.

The [digest HTTP authentication
scheme]({{ site.baseurl }}/digest-access-authentication/) may be used for
applications that have slightly more stringent security needs than those
provided by basic authentication, but would not benefit from the distributed
nature of OAuth.

Using the [oauth2_proxy]({{ site.baseurl }}/oauth/oauth2_proxy/) running on
the same host or within a private network may avoid the need to integrate
OAuth functionality into the application.
