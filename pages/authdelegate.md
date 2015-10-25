---
permalink: /authdelegate/
title: Auth delegation server
---
The [authdelegate server](https://github.com/18F/authdelegate) routes
requests to multiple authentication servers based on the presence of specific
headers or cookies in a request. The primary use case is to
[allow authenticated access by both humans and automated
systems]({{ site.baseurl }}/use-cases/human-and-system-access/).

View the README from the above link for details on how to run it manually, how
to configure it with the [Nginx web server](http://nginx.org/), and how to
configure it to serve traffic directly over [HTTPS]({{ site.baseurl }}/https).
