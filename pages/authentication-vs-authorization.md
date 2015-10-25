---
permalink: /authentication-vs-authorization/
title: Authentication vs. authorization
---
The bulk of this guide focuses on _authentication_, the act of validating the
identity of a request sender and the integrity of the request. This is
distinct from _authorization_, or deciding whether the sender has the
necessary privileges to make the request. Authorization depends on
authentication, but the concepts are distinct and are not interchangeable.

Therefore, throughout the guide, "authentication" by itself implies that an
authenticated request is implicitly authorized, whereas "authorization"
implies that a request has been authenticated and the sender has permission to
make the request.
