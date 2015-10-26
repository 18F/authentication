---
permalink: /use-cases/human-and-system-access/
title: Authorizing access by both humans and systems
parent: Use cases
---
To provide a combination of [OAuth]({{ site.baseurl }}/oauth/) (for humans) and
[HMAC]({{ site.baseurl }}/hmac/) (for machines) authentication, try the
[authentication delegation server]({{ site.baseurl }}/authdelegate/).

## Benefits

The authentication delegate server is easily configured to work with
[Nginx's `auth_request` directive](http://nginx.org/en/docs/http/ngx_http_auth_request_module.html).

This is particularly handy for authenticated APIs, as it allows humans to view
and manipulate the same API endpoints as a program that said human may be
trying to develop or debug.  

## Alternatives

A developer may run an instance of the [HMAC proxy
server]({{ site.baseurl }}/hmac/hmacproxy/) configured to produce the same
signatures as the server in order to view authenticated API endpoints in a
browser, or to send requests from a program that does not have HMAC
computation integrated (e.g. `curl`).

An application may integrate both the OAuth and HMAC schemes directly.
