---
permalink: /https/
title: HTTPS and SSL/TLS
---
[HTTPS](https://en.wikipedia.org/wiki/HTTPS) stands for _Hyper-Text Transport
Protocol Secure_, which is the mechanism for making secure
[HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) requests by
using [Secure Sockets Layer encryption (SSL, also known as Transport Layer
Security, or TLS)](https://en.wikipedia.org/wiki/Transport_Layer_Security).

HTTPS provides secrecy regarding the content of a request, including the
request method (GET, PUT, etc.), the URI of the requested resource, and any
tokens and signatures that implement the authentication mechanism, all in
addition to the request body itself. The only unencrypted components of the
request are the hostname (or IP address) and port, which are necessary to
route the request across the Internet.

HTTPS is a prerequisite for authentication, since none of the authentication
mechanisms encrypt the request, including the HTTP headers containing
authentication credentials. The initial encryption handshake is required to
authenticate the server to the client, and the encrypted connection is
required to authenticate the client to the server without leaking credentials,
reducing the likelihood of
[replay attacks]({{ site.baseurl }}/avoiding-replay-attacks/).
