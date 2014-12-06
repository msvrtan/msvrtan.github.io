---
layout: post
status: publish
published: true
title: Github and Trello integration
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 182
wordpress_url: http://www.mirosvrtan.me/blog/?p=182
date: '2012-10-21 12:12:42 +0000'
date_gmt: '2012-10-21 12:12:42 +0000'
categories:
- git
tags:
- git
- github
- trello
- integration
comments: []
permalink: /blog/2012/10/github-and-trello-integration/
---
<p>After working with git for more then 2 years, few months ago I decided to start using <a href="http://www.github.com" target="_blank">Github</a> to store my repos and test different workflow arrangements. It worked out great, I'm really happy with all it offers (it is a little bit pricy for my taste though) and I'm loving it.</p>
<p>In admin section of my repos some time ago I noticed unfamiliar term called 'Service Hooks' and decided to explore it. Service hooks are already prepared git post receive hooks for integration with other popular web services (<a href="https://help.github.com/articles/post-receive-hooks" target="_blank">description</a>) . Since I use <a href="https://trello.com/" target="_blank">Trello</a> for todo's on some of my pet projects I decided to connect this two webservices.</p>
<p>For easier demonstration I opened a new <a href="https://github.com/msvrtan/testing-trello-integration/" target="_blank">github repo</a>, <a href="https://trello.com/board/testing-trello-github-integration/5083d2888fb535b871008eb2" target="_blank">Trello board</a> and connected them.</p>
<p><img alt="Trello board for testing integration" src="http://www.mirosvrtan.me/blog/wp-content/uploads/2012/10/trello-board-for-testing-integration-with-github.png" width="500px" /></p>
<p><img alt="github project for testing trello integration" src="http://www.mirosvrtan.me/blog/wp-content/uploads/2012/10/github-project-for-testing-trello-integration.png"  width="500px" /></p>
<p>Now every new commit on master branch is shown in list 'Commits on master' and new pull requests in 'Pull requests'. It is really simple but effective way of tracking stuff to do on smaller projects, I hope to be able to test it very soon in a little bit larger environment though.</p>
<p>It is really easy to setup, after allowing github to access your Trello account via token you can add new pull requests cards to different board then commit cards. It also features ignoring some commits from creation by tracking only master branch or by setting up regular expressions.</p>
<p><img alt="Trello service hook form on github" src="http://www.mirosvrtan.me/blog/wp-content/uploads/2012/10/Screenshot.png" width="300px" /></p>
<p><em>Short guide with 4 steps is located under the form (not shown on screenshot here).</em></p>
<p>One crucial thing missing here is integration of issues. It would be very helpful if issues could be sent too but this is something I'm currently testing with <a href="https://zapier.com/" target="_blank">Zapier</a> (and much more but this will be subject for one of next posts :).</p>
<p>Feel free to fork repository &amp; generate pull requests, this repository and board are used only for demonstration purposes!</p>
