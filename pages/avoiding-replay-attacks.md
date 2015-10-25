---
permalink: /avoiding-replay-attacks/
title: Avoiding replay attacks
---
[Replay attacks](https://en.wikipedia.org/wiki/Replay_attack) occur when a
previously authenticated and authorized request is sent multiple times. Such
attacks consist of an unauthorized third party eavesdropping on a request
and acquiring access to protected information (either downloading or
destroying it), or in that party launching a [denial of
service](https://en.wikipedia.org/wiki/Denial-of-service_attack)
attack that leads to internal resource exhaustion. Replay attacks can prove
particularly damaging if a replayed request is an API call that allocates,
modifies, or destroys expensive or critical internal application resources.

## HTTPS as a prerequisite

The first line of defense against such attacks is the diligent use of
[HTTPS]({{ site.baseurl }}/https/), which encrypts headers and cookies
containing authentication inputs, tokens, and signatures, in addition to the
request body itself.

## Advanced defense mechanisms

Other lines of defense consist of using unique server-provided [session
tokens](https://en.wikipedia.org/wiki/Session_token) or similar artifacts
([one-time passwords (OTPs)](https://en.wikipedia.org/wiki/One-time_password),
[nonces](https://en.wikipedia.org/wiki/Cryptographic_nonce)) that the sender
must incorporate as an input to the authentication mechanism, or time-based
mechanisms.

As an example of a time-based mechanism (from the Wikipedia article referenced
above), the sender may be required to include an estimate of the receiver's
system time in the request, whereby the receiver will only accept requests
within a certain window of time. When requests _must_ occur once and only
once, this may be a more efficient means of preventing replay attacks than
maintaining a database of previously-seen requests.

There may be a legitimate use case for repeating previously-sent requests,
such as [refiring webhooks]({{ site.baseurl }}/use-cases/webhooks/). In this
case, the receiving application may maintain a fixed-size hash table of recent
request signatures mapped to the time they were last received, effectively
throttling the frequency of repeated requests.
