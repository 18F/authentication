---
permalink: /use-cases/api-access/
title: Authorizing API access
parent: Use cases
---
[Application Programming Interfaces
(APIs)](https://en.wikipedia.org/wiki/Application_programming_interface) are
web application endpoints that either provide data to client applications or
that induce the server application to perform an action. In both cases, there
may be a need to restrict access to authorized users.

In most cases, since APIs are consumed by automated systems, an API provider
will provide an [API
key](https://en.wikipedia.org/wiki/Application_programming_interface_key) that
identifies the client and acts as a shared secret. Some API providers such as
Amazon will require that the key be used to produce a
[HMAC signature]({{ site.baseurl }}/hmac/) of the request content.

## Benefits

API keys help track usage as well as identify potential abuse.

HMAC signatures ensure that the content of an API request was sent by an
authorized client and was not modified during transmission.

The HMAC signature or other identifier may be used to prevent
[replay attacks]({{ site.baseurl }}/avoiding-replay-attacks/).

## Alternatives

There may be no need to authenticate access to an API, particularly for a
public data API such as the [18F public Team
API](https://team-api.18f.gov/public/api/).
