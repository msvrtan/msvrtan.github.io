---
layout: post
status: publish
published: true
title: Importing data from compressed files directly to MySQL
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 363
wordpress_url: http://www.mirosvrtan.me/blog/?p=363
date: '2013-02-05 19:59:19 +0000'
date_gmt: '2013-02-05 18:59:19 +0000'
categories:
- mysql
tags:
- mysql
- tips and tricks
- linux
comments: []
permalink: /blog/2013/02/importing-data-from-compressed-files-directly-to-mysql/
---
<p>This is a neat trick for directly importing compressed MySQL dump files into MySQL</p>
<p>&nbsp;</p>
<pre lang="bash">xz -dc /folder-of-my-choice/filename.xz | mysql -u username -pmy_password</pre><br />
&nbsp;</p>
<p>It might not be of much use to everyone, but if you found yourself in situation where you first had to uncompress a few GB file and then import it this will really speed up the process.</p>
<p>Key option here is '<strong>-c' </strong>which enables decompressing to standard output and '|' allows us to send that data directly into MySQL importer. Though this example is using xz tool,&nbsp; most uncompressing tools should have a similar option.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
