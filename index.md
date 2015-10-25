---
permalink: /
title: Introduction
---
HTTP authentication is the means by which the receiver of a HTTP request can
verify the legitimacy of the sender and the integrity of the request.
Authentication is crucial to preventing unauthorized access to systems, and
may serve to mitigate the effects of a denial of service attack by rejecting
requests that fail authentication prior to further processing.

This guide describes some of the basics of HTTP request authentication and its
use in 18F's systems. It covers the
[basic]({{ site.baseurl }}/basic-access-authentication/),
[digest]({{ site.baseurl }}/digest-access-authentication/), and
[OAuth]({{ site.baseurl }}/oauth/) authentication schemes listed in the
[Hypertext Transfer Protocol Authentication Scheme
Registry](http://www.iana.org/assignments/http-authschemes/http-authschemes.xhtml)
referenced by [RFC 7235, _Hypertext Transfer Protocol (HTTP/1.1):
Authentication_](http://tools.ietf.org/html/rfc7235), as well as the
[Hash-based Message Authentication Code]({{ site.baseurl }}/hmac/) scheme
employed by many web service providers.

## Help improve this guide

As security is a vast and rapidly changing subject, _review by and
contributions from the broader security community are extremely welcome_, both
to this guide and to the open source software described within. Links to the
[18F/authentication GitHub Repository](https://github.com/18F/authentication)
to suggest edits or open issues for discussion may be found in the footer of
every page.
