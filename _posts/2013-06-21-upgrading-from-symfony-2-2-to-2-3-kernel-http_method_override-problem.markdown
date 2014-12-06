---
layout: post
status: publish
published: true
title: Upgrading from Symfony 2.2 to 2.3
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 430
wordpress_url: http://www.mirosvrtan.me/blog/?p=430
date: '2013-06-21 20:06:43 +0000'
date_gmt: '2013-06-21 19:06:43 +0000'
categories:
- php
tags:
- php
- symfony 2
- sf 2.3
comments:
- id: 4874
  author: Jorge
  author_email: jorge.hernan@radmas.com
  author_url: ''
  date: '2013-07-04 08:47:04 +0000'
  date_gmt: '2013-07-04 07:47:04 +0000'
  content: "Hi. I got the same error, but it doesn't fix deleting cache.\r\n\r\nDo
    you know how can i fix that?\r\n\r\nThanks !"
---
<p>After upgrading from Symfony 2.2 to 2.3, when I would try to purge production cache with</p>
<p><code lang="php"><br />
php app/console cache:clear --env=prod --no-debug<br />
</code></p>
<p>I got error saying:</p>
<p><a href="http://www.mirosvrtan.me/blog/wp-content/uploads/2013/06/symfony2.3kernel.http_method_override.error_.png"><img src="http://www.mirosvrtan.me/blog/wp-content/uploads/2013/06/symfony2.3kernel.http_method_override.error_.png" alt="symfony2.3kernel.http_method_override.error" width="648" height="99" class="alignleft size-full wp-image-432" /></a></p>
<p><code lang="php"><br />
[Symfony\Component\DependencyInjection\Exception\InvalidArgumentException]<br />
The parameter "kernel.http_method_override" must be defined.</code></p>
<p>For some strange reason this error happens only in production mode, I found out that deleting <strong>"app/cache/prod"</strong> folder and all of its contents solves it.</p>
<p>P.S. This was only problem I had with upgrading from 2.2 to 2.3 so upgrade went pretty smoothly..</p>
