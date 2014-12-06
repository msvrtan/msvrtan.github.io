---
layout: post
status: publish
published: true
title: Oracle Java 7 for faster PhpStorm on Ubuntu Linux
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 159
wordpress_url: http://www.mirosvrtan.me/blog/?p=159
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
---
<p>
Since PhpStorm works much faster with Oracle version of Java and Oracle JRE is not directly supported in Ubuntu here are 3 short steps how to get it:<br />
<&#47;p></p>
<pre lang="bash">
sudo add-apt-repository ppa:webupd8team&#47;java<br />
sudo apt-get update<br />
sudo apt-get install oracle-java7-installer<br />
<&#47;pre></p>
<p>
That's it... don't be a hero like me and try to run PhpStorm with OpenJRE, it is really slow :(<br />
<&#47;p></p>
