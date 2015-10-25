---
permalink: /use-cases/sso/
title: Authorizing application access via Single Sign-On
parent: Use cases
---
For a family of applications used internally by an organization, it is
possible to configure Single Sign-On (SSO) credentials so that a single login
credential serves to authorize (or not) access to every system, rather than
requiring a separate login for each. Each internal application may contain
logic to process an OAuth token from an authentication system such as MyUSA,
Google Accounts, GitHub, etc., and every application can use the same API key.

## Benefits

All members of an organization need sign in only once and grant access only
once to an organization's entire suite of applications.

## Alternatives

The [oauth2_proxy]({{ site.baseurl }}/oauth/oauth2_proxy/) can allow a single
application key to cover all internal applications, without requiring each
application to integrate OAuth functionality. It can be configured to
securely forward authenticated credentials to upstream applications without
contacting the OAuth provider, amongst other convenient features.
