---
layout: post
status: publish
published: true
title: 'Removing duplicated records in MySQL '
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 198
wordpress_url: http://www.mirosvrtan.me/blog/?p=198
date: '2012-10-24 14:22:02 +0000'
date_gmt: '2012-10-24 14:22:02 +0000'
categories:
- mysql
tags:
- mysql
- tips and tricks
comments: []
---
<p>Colleague just pointed out cool way of removing duplicate entries in MySQL. We had a 'small' problem in one table where some records got duplicated since we forgot to add UNIQUE index.</p>
<p>So if you want to remove from table "<strong>my_favorite_table</strong>" all duplicated records and add forgotten unique index use "<strong>ALTER IGNORE TABLE</strong>" instead of "<strong>ALTER TABLE</strong>":</p>
<pre lang="sql">ALTER IGNORE TABLE my_favorite_table ADD UNIQUE INDEX name_of_my_unqique_index(column_1, column_2)</pre><br />
Thanks go to Luka Skupnjak for pointing out this cool trick!</p>
