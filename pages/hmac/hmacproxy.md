---
permalink: /hmac/hmacproxy/
title: HMAC proxy server
parent: Hash-based Message Authentication Codes
---
The [hmacproxy server](https://github.com/18F/hmacproxy/) is a command-line
tool for either signing outbound requests or authenticating inbound requests
using [HMAC signatures](..). While handy as a development tool, it is a
production-ready authentication and proxy server.

View the README from the above link for details on how to run it manually, how
to configure it with the [Nginx web server](http://nginx.org/), and how to
configure it to serve traffic directly over [HTTPS]({{ site.baseurl }}/https).
