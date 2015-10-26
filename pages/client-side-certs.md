---
permalink: /client-side-certs/
title: Client-side certs
---

Much as users's browsers authenticate the servers they connect to during a TLS
handshake, the server can also authenticate the user. While this isn't
something typically used in browsers, it might be a good option for
authenticating machine-to-machine conversations.

At the high level, a client certificate is generated and installed in the
web server. The server is then configured to either hard-fail, rejecting any
traffic with an invalid or non-existing cert, or soft-fail, where the presence
or absence of a client-side certificate (and perhaps, e.g. it's fingerprint)
are passed along to the application. When making requests, the client must
present the certificate.

## Advantages

Part of the TLS standard, providing well vetted, solid crypto.

Authentication can be orthogonal to the rest of the application logic, if
desired.

## Drawbacks

Difficult to implement, particularly if behind a load balancer or similar
proxy.

Many HTTP request libraries do not implement client-side certificates.
