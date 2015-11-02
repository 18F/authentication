---
permalink: /hmac/
title: Hash-based Message Authentication Codes
---
[Hash-based Message Authentication Codes](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code),
aka HMAC signatures, are cryptographic signatures based on:

- a hash algorithm such as SHA-1,
- a secret key shared between the sender and the receiver, and
- various components of a HTTP request, such as:
  - the HTTP method (GET, POST, PUT, UPDATE, DELETE, HEAD),
  - the URL or a subcomponent thereof (e.g. everything following the host name),
  - a specific combination of HTTP headers, and
  - the request body.

They serve to both authenticate the sender to the receiver and validate the
integrity of a request, because the sender and receiver should compute
identical hash values given the same algorithm, secret key, and request. The
basic flow is:

- A client makes a request for a protected resource by producing a
  cryptographic signature of the request and adding this signature to a header.
- The server computes a signature from the request.
- If the server's computed signature matches that supplied by the sender, the
  request is authenticated and permitted to pass through to the rest of the
  application. Otherwise, the request is denied.

## Delimiters required

When building the string that will be used as input to the hash algorithm,
there _must_ be a delimiter between input fields to signal the presence of
empty inputs. Otherwise, the potential for multiple requests hashing to the
same signature is increased. For example, a request that contains input
headers such as:

```
X-Input-0: foo
X-Input-1: bar
```

may produce the same hash as request containing only `X-Input-0: foobar` or
`X-Input-1: foobar`, since the concatenated values in all three cases will
produce the string `foobar`. By forcing a delimiter such as `\n`, the three
requests will produce `foo\nbar`, `foobar\n`, and `\nfoobar`, respectively,
all producing different hash values.

## Advantages

This scheme is easy to implement on both the client and server side.

In addition to authenticating the identity of the client, it can also provide
validation of the integrity of the request, i.e. that the request has not been
altered during transmission.

It is ideal for requests between systems that do not require human
intervention or specific user authorization.

When using [oauth2_proxy]({{ site.baseurl }}/oauth/oauth2_proxy/) as a
[Single Sign-On]({{ site.baseurl }}/use-cases/sso/) mechanism, the user only
needs to grant permission once to access multiple applications authenticated
using the proxy, which can be used to provide an
[intranet without a VPN]({{ site.baseurl }}/use-cases/intranet-without-vpn/).

## Drawbacks

The shared key must be carefully managed.

There is no canonical implementation. GitHub's
[Webhooks](https://developer.github.com/webhooks/securing/) only considers the
request payload; Amazon
[requires](http://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAuthentication.html)
a separate time stamp field, etc. etc.

The string used to produce the cryptographic signature must be carefully
constructed to avoid having different requests produce the same hash value.

Straightforward implementations read the entire request body into memory to
compute the signature. Large request bodies will require a more complex
implementation, or should be dropped by the server before signature
computation.

[Replay attacks]({{ site.baseurl }}/avoiding-replay-attacks/) are possible if
there isn't an additional nonce check. When combined with TLS, however, we
guarantee authentication, integrity, and confidentiality.


## Further reading

- [Amazon Web Services, _Signing and Authenticating REST
  Requests_](https://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAuthentication.html)
- [rc3.org, _Using HMAC to authenticate Web service
  requests](http://rc3.org/2011/12/02/using-hmac-to-authenticate-web-service-requests/)
