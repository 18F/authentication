---
permalink: /use-cases/
title: Use cases
---
HTTP authentication is useful for a number of situations where the receiver of
a request must be certain that the request was sent from a legitimate source,
and digital signatures can ensure that a request not altered during
transmission.

## Authentication vs. authorization

The bulk of this guide focuses on _authentication_, the act of validating the
identity of a request sender and the integrity of the request. This is
distinct from _authorization_, or deciding whether the sender has the
necessary privileges to make the request. Authorization depends on
authentication, but the concepts are distinct and are not interchangeable.

Therefore, in the language below, "authentication" by itself implies that all
authenticated requests are implicitly authorized, whereas "authorization"
implies that requests have been authenticated and the sender has permission to
make the request.

## Authorizing user access to applications

This is a very familiar use case, whereby a human user logs into an
application and maintains a credential that permits access to part or all of
that application. This is the use case covered by the
[OAuth protocol]({{ site.baseurl }}/oauth/).

## Authorizing application access via Single Sign-On

For a family of applications used internally by an organization, it is
possible to configure Single Sign-On (SSO) credentials so that a single login
credential serves to authorize (or not) access to every system, rather than
requiring a separate login for each.

There are a number of ways to do this. Each internal application may contain
logic to process an OAuth token from an authentication system such as MyUSA,
Google Accounts, GitHub, etc., and every application can use the same API key.

Alternatively, proxy servers such as [bitly/oauth2_proxy]({{ site.baseurl }}/oauth/oauth2_proxy/)
can provide flexibility in how OAuth credentials are shared across
applications, and can even provide authentication for static web sites,
described next.

## Authorizing access to static web sites

Static web sites are comprised of pre-generated HTML pages and other files
that can be served directly by a standard web server, and therefore contain no
logic of their own to authenticate and authorize requests. By definition, they
do not contain application logic that can authenticate or authorize requests.

However, common web servers such as [Nginx](http://nginx.org/) provide the
capability to proxy requests through servers such as
[bitly/oauth2_proxy]({{ site.baseurl }}/oauth2_proxy/), and configured
properly, a single proxy can authorize access to any number of static sites.

Its capability to authenticate and authorize the sender of a request, to add
authenticated user information to a request, and cryptographically sign the
request before passing it upstream also enables it to also be used by other
web applications as an alternative to integrating OAuth libraries directly.

## Authenticating webhooks

Webhooks are automated notifications containing information about configured
events, sent to a server listening for them. The server then may ignore the
events, or take action based on the information contained in the request.

While the content of the request may contain information used to decide
whether or not to take action, authorization may be implied by
[cryptographic signatures]({{ site.baseurl }}/hmac/) rather than a protocol
such as OAuth, allowing for a lighter-weight authentication implementation.

Several 18F projects make use of [GitHub webhooks](https://developer.github.com/webhooks/)
to take automated action when activity takes place in our repositories. The
[GitHubguide to securing webhooks](https://developer.github.com/webhooks/securing/)
contains concrete instructions on how to configure and authenticate secure
GitHub webhook requests.

## Authorizing access to internal APIs

## Authorizing API access by both humans and systems
