---
permalink: /use-cases/webhooks/
title: Authenticating webhooks
parent: Use cases
---
Webhooks are automated notifications containing information about configured
events, sent to a server listening for them. The server then may ignore the
events, or take action based on the information contained in the request.

While the content of the request may contain information used to decide
whether or not to take action, authorization may be implied by
[cryptographic signatures]({{ site.baseurl }}/hmac/) rather than a protocol
such as [OAuth]({{ site.baseurl }}/oauth/), allowing for a lighter-weight
authentication implementation.

Several 18F projects make use of [GitHub webhooks](https://developer.github.com/webhooks/)
to take automated action when activity takes place in our repositories. The
[GitHub guide to securing webhooks](https://developer.github.com/webhooks/securing/)
contains concrete instructions on how to configure and authenticate secure
GitHub webhook requests.

## Benefits

Systems may make secure, authenticated requests to other systems over
[HTTPS]({{ site.baseurl }}/https/), enabling the implementation of an
[intranet without a VPN]({{ site.baseurl }}/use-cases/intranet-without-vpn).

Automated workflows may be triggered in a secure fashion without human
intervention.

HMAC implementation and management is less complex than comparable OAuth
schemes.

## Alternatives

OAuth providers may grant tokens for use by automated systems, but the way in
which they are acquired and managed varies, adding extra complexity to
applications that incorporate them.
