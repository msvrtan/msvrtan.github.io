---
layout: post
status: publish
published: true
title: Oracle Java 7 for faster PhpStorm on Ubuntu Linux
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 159
wordpress_url: https://www.mirosvrtan.me/blog/?p=159
date: '2012-09-15 23:06:02 +0000'
date_gmt: '2012-09-15 23:06:02 +0000'
categories:
- php
tags:
- php
- phpstorm
- oracle java
- ubuntu
- how to
- install
comments: []
permalink: /blog/2012/09/oracle-java-7-for-faster-phpstorm-on-ubuntu-linux/
---
<p>
Since PhpStorm works much faster with Oracle version of Java and Oracle JRE is not directly supported in Ubuntu here are 3 short steps how to get it:<br />
</p></p>
<pre lang="bash">
sudo add-apt-repository ppa:webupd8team/java<br />
sudo apt-get update<br />
sudo apt-get install oracle-java7-installer<br />
</pre></p>
<p>
That's it... don't be a hero like me and try to run PhpStorm with OpenJRE, it is really slow :(<br />
</p></p>
