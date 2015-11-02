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
request are the IP address (and hostname if using
[SNI](https://en.wikipedia.org/wiki/Server_Name_Indication)) and port, which
are necessary to route the request across the Internet.

HTTPS ensures confidentiality and integrity, which are generally assumed for
the authentication methods described here. Unless explicitly told otherwise,
clients which initiate an HTTPS request will verify the validity of the
server's certificate. In this regard, the client can be relatively certain
that the server is who it claims to be. The same system can be used by servers
to [validate]({{ site.baseurl }}/client-side-certs/) a client's identity. TLS
connections are not vulnerable to
[replay attacks]({{ site.baseurl }}/avoiding-replay-attacks/); an eavesdropper
cannot replay packets on the wire to any ill effect.
