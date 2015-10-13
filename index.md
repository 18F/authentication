---
permalink: /
title: Introduction
---
HTTP authentication is the means by which the receiver of a HTTP request can
verify the legitimacy of the sender and the integrity of the request.
Authentication is critical to preventing unauthorized access to systems, and
may serve to mitigate the effects of a denial of service attack by rejecting
requests that fail authentication prior to further processing.

This guide describes some of the basics of HTTP request authentication and its
use in 18F's systems.

## Basic components

A [HTTPS connection]({{ site.baseurl }}/https/) between the sender and receiver
is a requirement for all use cases.

Many systems rely on [authentication tokens]({{ site.baseurl }}/oauth/) that
identify a resource owner (human, organization, or application) and grant the
receiving application access to various components of the owner's identity for
further [authorization]({{ site.baseurl }}/authentication-vs-authorization/),
without exposing the owner's credentials.

As an alternative, [cryptographic signatures]({{ site.baseurl }}/hmac/) created
using a hash algorithm, a secret key, and a combination of values from the
request may be used to authenticate individual requests. These signatures are
particularly useful for requests made between automated systems.

- The sender adds a signature to the request based upon inputs such as:
  - the HTTP method (GET, POST, PUT, UPDATE, DELETE, HEAD),
  - the URL or a subcomponent thereof (e.g. everything following the host name),
  - a specific combination of HTTP headers, and
  - the request body.
- The receiver computes its own signature for the request using the same hash
  algorithm, secret key, and request values used by the sender

The receiver computes the request signature as the first step of its
application flow. If the receiver's computed signature matches that supplied
by the sender, the request is authenticated and permitted to pass through to
the rest of the application. Otherwise, the request is denied.

## Help improve this guide

As security is a vast and rapidly changing subject, _review by and
contributions from the broader security community are extremely welcome_, both
to this guide and to the open source software described within. Links to the
[18F/authentication GitHub Repository](https://github.com/18F/authentication)
to suggest edits or open issues for discussion may be found in the footer of
every page.
