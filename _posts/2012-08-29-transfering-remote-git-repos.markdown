---
layout: post
status: publish
published: true
title: Transfering remote GIT repos
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 151
wordpress_url: http://www.mirosvrtan.me/blog/?p=151
date: '2012-08-29 21:59:05 +0000'
date_gmt: '2012-08-29 21:59:05 +0000'
categories:
- git
tags:
- git
- development
- github
comments: []
---
<p>When we switched from SVN to GIT we decided to have one central repo to ease workflow to developers (extra complexity with everyone having forked remote repo would have been to much at that point). Today I had to copy that main repo to github but it had >50 branches and there was no way I would clone this repo and push branch by branch. I'm just too lazy :) Next idea was to generate a shell script doing this but I was hoping to find some better solution. And I found it. It is '--all' option on push!</p>
<p>There are 2 possibilities how to do it:</p>
<p>1) Create local mirror repo (if you clone push will work only on branches you checked out here)</p>
<pre lang="bash">cd some-folder<br />
git clone --mirror git@example.com&#47;my-main-repo.git<br />
cd my-main-repo<br />
git remote add github git@github.com:my-username&#47;my-new-main-repo.git<br />
git push github --all<&#47;pre><br />
2) Directly from bare remote repo</p>
<pre lang="bash">ssh example.com<br />
cd my-main-repo.git<br />
git remote add github git@github.com:my-username&#47;my-new-main-repo.git<br />
git push github --all<br />
git remote rm github<&#47;pre><br />
I went with idea #2 since our server has much better internet connection then my home desktop but idea #1 is great one if you are not able to ssh yourself to remote server (lets say you want to transfer from bitbucket, assembla or github anywhere).</p>
<p>Just a notice that this is not github feature, it will work everywhere :)</p>
