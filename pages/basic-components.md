---
permalink: /basic-components/
title: Basic components
---
A [HTTPS connection]({{ site.baseurl }}/https/) between the sender and receiver
is a requirement for _all_ use cases, since none of the mechanisms provide
encryption of the request itself. Also, HTTPS enables the client to
authenticate the server's identity when establishing the initial connection,
and subsequently enables the server to authenticate the client's identity over
the secure connection.

Several systems rely on passwords or unique authentication tokens. These
tokens usually must be refreshed after some period of time. Standard HTTP
schemes such as 
[basic]({{ site.baseurl }}/basic-access-authentication/) and
[digest]({{ site.baseurl }}/digest-access-authentication/) require the server
to manage client identity credentials, while
[OAuth]({{ site.baseurl }}/oauth/) schemes enable third-party providers to
manage a client's identity across multiple distributed applications on
different hosts.

As an alternative, [cryptographic signatures]({{ site.baseurl }}/hmac/) created
using a hash algorithm, a secret key, and a combination of values from the
request may be used to authenticate individual requests from trusted clients.
The secret key need not expire, necessarily. These signatures are particularly
useful for requests made between systems that require no human intervention.
