---
layout: post
status: publish
published: true
title: Upgrading from Symfony 2.2 to 2.3
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 430
wordpress_url: https://www.mirosvrtan.me/blog/?p=430
date: '2013-06-21 20:06:43 +0000'
date_gmt: '2013-06-21 19:06:43 +0000'
categories:
- php
tags:
- php
- symfony 2
- sf 2.3
comments: []
permalink: /blog/2013/06/upgrading-from-symfony-2-2-to-2-3-kernel-http_method_override-problem/
---
<p>After upgrading from Symfony 2.2 to 2.3, when I would try to purge production cache with</p>
<p><code lang="php">
php app/console cache:clear --env=prod --no-debug
</code></p>
<p>I got error saying:</p>
<p><a href="https://www.mirosvrtan.me/assets/content/uploads/2013/06/symfony2.3kernel.http_method_override.error_.png"><img src="https://www.mirosvrtan.me/assets/content/uploads/2013/06/symfony2.3kernel.http_method_override.error_.png" alt="symfony2.3kernel.http_method_override.error" width="648" height="99" class="alignleft size-full wp-image-432" /></a></p>
<p><code lang="php">
[Symfony\Component\DependencyInjection\Exception\InvalidArgumentException]<br />
The parameter "kernel.http_method_override" must be defined.</code></p>
<p>For some strange reason this error happens only in production mode, I found out that deleting <strong>"app/cache/prod"</strong> folder and all of its contents solves it.</p>
<p>P.S. This was only problem I had with upgrading from 2.2 to 2.3 so upgrade went pretty smoothly..</p>
