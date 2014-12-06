---
layout: post
status: publish
published: true
title: 'Installing ElasticSearch on Linux Ubuntu 12.04 & Mint 14 '
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 461
wordpress_url: http://www.mirosvrtan.me/blog/?p=461
date: '2014-01-02 17:18:46 +0000'
date_gmt: '2014-01-02 16:18:46 +0000'
categories:
- Uncategorized
tags:
- elasticsearch
- search
- devops
comments: []
---
<p>Since Oracle Java is not shipped with Debian based distributions due to licencing issues, you must setup it manually via PPA repositories.</p>
<pre lang="bash">
apt-get install python-software-properties -y<br />
add-apt-repository ppa:webupd8team&#47;java<br />
apt-get update<br />
apt-get install oracle-java7-installer<br />
<&#47;pre></p>
<p>After Java is installed, go to <a href="http:&#47;&#47;elasticsearch.org&#47;download&#47;" target="_blank"> ElasticSearch download page<&#47;a> and download deb package.</p>
<pre lang="bash">
wget https:&#47;&#47;download.elasticsearch.org&#47;elasticsearch&#47;elasticsearch&#47;elasticsearch-0.90.9.deb<br />
dpkg -i elasticsearch-0.90.9.deb</p>
<p><&#47;pre></p>
<p>At this moment (Jan 2014) 0.90.9 is latest version of ElasticSearch. Thats it. You have ElasticSearch installed!</p>
