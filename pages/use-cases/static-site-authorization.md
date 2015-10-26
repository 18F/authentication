---
permalink: /use-cases/static-site-authorization/
title: Authorizing access to static web sites
parent: Use cases
---
Static web sites are comprised of pre-generated HTML pages and other files
that can be served directly by a standard web server, and therefore contain no
logic of their own to authenticate and authorize requests. However, common web
servers such as [Nginx](http://nginx.org/) provide the capability to proxy
requests through servers such as [oauth2_proxy]({{ site.baseurl }}/oauth2_proxy/).

## Benefits

Static sites benefit from the power and security of
[OAuth]({{ site.baseurl }}/oauth/).

Multiple static sites can be served by a single `oauth2_proxy` instance.

## Alternatives

The [basic]({{ site.baseurl }}/basic-access-authentication/) and
[digest]({{ site.baseurl }}/digest-access-authentication/) HTTP authentication
schemes may be used instead. While providing less power and flexibility, they
do not require the configuration of a separate server (though `oauth2_proxy`
is really very easy to manage).
