---
permalink: /basic-access-authentication/
title: Basic access authentication
---
This form of authentication is defined in [RFC 7617, _The 'Basic' HTTP
Authentication Scheme_](http://tools.ietf.org/html/rfc7617). The basic flow
is:

- An as-yet-unauthenticated client makes a request for a protected resource.
- The server returns a [401 status
  code](http://tools.ietf.org/html/rfc2616#section-10.4.2) along with a
  header of the format: `WWW-Authenticate: Basic realm="REALM_ID"`, where
  `REALM_ID` somehow identifies the "protection space" of the requested
  resource.
- The client resends the request with a header of the format
  `Authorization: Basic BASE64_ENCODED_VALUE`, where the `BASE64_ENCODED_VALUE`
  is a string of the format `username:password` in [Base64
  encoding](https://en.wikipedia.org/wiki/Base64).
- The server either grants or denies access to the requested resource.

## Advantages

This is a relatively easy authentication scheme to implement, as common web
servers such as
[Nginx](http://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) and
[Apache](https://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html) provide
straightforward configuration mechanisms. Similarly, libraries exist for
verifying this at the application layer.

It is thoroughly understood and has been tested for years.

If using a long user name and password composed of random strings, Basic Auth
is on par with including an API key with each request.

## Drawbacks

The Base64-encoded `username:password` value is not encrypted, and provides no
validation of the integrity of the request.

If authenticating an end user, most browsers will prompt the user for input.
The browser then caches the challenge response for subsequence requests. There
is no explicit logout mechanism.

There is no automatic sharing of credentials from system to system.

Though, when combined with TLS, authentication, integrity, and confidentiality
is ensured, there's a high risk for accidentally leaking credentials. Consider
that, a missing "s" in a curl command would reveal the credentials.
