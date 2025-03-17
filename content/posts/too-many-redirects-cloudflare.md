+++
date = '2025-03-16T17:44:27+07:00'
draft = false
title = 'ERR_TOO_MANY_REDIRECTS on Cloudflare'
+++

When you turn on the `proxy` feature on Cloudflare and you get the error `ERR_TOO_MANY_REDIRECTS`. Solve by doing this:

1. Go to the site configuration on Cloudflare
2. `SSL > Overview`
3. `SSL Encryption` section and `Configure`
4. Select `Full`

Done.
