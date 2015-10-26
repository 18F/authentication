---
permalink: /oauth/oauth2_proxy/
title: oauth2_proxy
parent: Oauth
---
The [`oauth2_proxy`](https://github.com/bitly/oauth2_proxy/) is an open-source
reverse proxy and static file server from Bitly that provides authentication
using configurable providers (Google, GitHub, LinkedIn, and MyUSA) to
authenticate accounts by email, domain or group. 18F currently uses it to
authenticate the [Hub](https://hub.18f.gov/), [Tock](https://tock.18f.gov/), and
the [Team API](https://team-api.18f.gov/api/).

Its capability to authenticate and authorize the sender of a request, to add
authenticated user information to a request, and cryptographically sign the
request before passing it upstream also enables it to also be used by other
web applications as an alternative to integrating OAuth libraries directly.
(_Note: These behaviors are currently pending in
[#147](https://github.com/bitly/oauth2_proxy/pull/147) and
[#153](https://github.com/bitly/oauth2_proxy/pull/153)._)
