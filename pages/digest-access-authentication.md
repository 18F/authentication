---
permalink: /digest-access-authentication/
title: Digest access authentication
---
This form of authentication is defined in [RFC 7616, _HTTP Digest Access
Authentication_](http://tools.ietf.org/html/rfc7616). The basic flow
is:

- An as-yet-unauthenticated client makes a request for a protected resource.
- The server returns a [401 status
  code](http://tools.ietf.org/html/rfc2616#section-10.4.2) along with a
  header of the format: `WWW-Authenticate: Digest ...`, where `...` contains
  a comma-separated list of `key=value` parameters including a hash algorithm
  and a [nonce](https://en.wikipedia.org/wiki/Cryptographic_nonce), a
  server-generated, unique, single-use token that the client must factor into
  its response.
- The client resends the request with a header of the format
  `Authorization: Digest ...`, where `...` contains a comma-separated list of
  `key=value` parameters including a `response` field that is a digest of the
  client's username, password, and other factors using the server-supplied
  hash algorithm, encoded in hexadecimal format.
- The server either grants or denies access to the requested resource.

## Advantages

The authentication and authorization is more robust than
[basic authentication]({{ site.baseurl }}/basic-access-authentication/), as
the access credentials are securely hashed and recomputed for every request.

Modules implementing digest authentication exist for
[Nginx](https://www.nginx.com/resources/wiki/modules/auth_digest/) and
[Apache](http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html).

## Drawbacks

The implementation is significantly more complex than basic authentication,
and the client's password must still be managed by the server.

The user must still be prompted for a password, which the browser or user
agent must manage.

There is no validation of the integrity of the request.
