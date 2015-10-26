---
permalink: /use-cases/intranet-without-vpn/
title: Intranet without VPN
parent: Use cases
---
By integrating [OAuth]({{ site.baseurl }}/oauth/) and/or
[HMAC]({{ site.baseurl }}/hmac/) capabilities into your applications, it is
possible to achieve the effect of having an intranet without configuring a
[virtual private network (VPN)](https://en.wikipedia.org/wiki/Virtual_private_network).

This is particularly of interest to 18F, as our standard
[Cloud.gov](https://cloud.gov/) platform, built on [Cloud
Foundry](https://www.cloudfoundry.org/), does not incorporate VPNs or inbound
traffic firewalls into its model. On this platform, developing both internal
and public-facing applications that can securely share data across the public
internet requires a robust application of OAuth and HMAC mechanisms.

## Benefits

Our internal applications are always available to every team member via the
public internet, but remain secure.

Our applications can share data securely without requiring a private network.

No administration of private networks of any kind.

## Alternatives

Given that cloud.gov/Cloud Foundry does not allow for private networks, or
even incoming firewall rules, there are none.
