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
comments:
- id: 2869
  author: Torsten Feld
  author_email: torsten@torsten-feld.de
  author_url: ''
  date: '2013-01-11 09:31:59 +0000'
  date_gmt: '2013-01-11 08:31:59 +0000'
  content: "Hi, nice article. I'm looking for a nice integration of GitHub and Trello
    for some time now. I mainly would like to use it for GitHub issues as I use Trello
    as some kind of backlog and release planner.\r\n\r\nActually, I do not even get
    the point of using currently available service hook for creating a trello card
    for every commit... \r\n\r\nBest regards,\r\nTorsten"
- id: 3279
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2013-01-22 23:36:58 +0000'
  date_gmt: '2013-01-22 22:36:58 +0000'
  content: "Hi,\r\n\r\nCard for each commit can be usefull if every commit needs to
    be reviwed, but in general I aggree with you. Issues and pull requests into cards
    would be much more usefull.\r\n\r\nSorry for a late response..\r\n\r\nMiro"
- id: 4130
  author: Bob
  author_email: bawbgale@gmail.com
  author_url: ''
  date: '2013-03-14 22:49:50 +0000'
  date_gmt: '2013-03-14 21:49:50 +0000'
  content: Did you ever work out how to integration GitHub Issues with Trello? I'm
    trying to use Trello as the one place where everyone looks for priorities, including
    bug fixes.
- id: 4972
  author: Adam
  author_email: adam.wamai@gmail.com
  author_url: ''
  date: '2013-07-16 04:02:10 +0000'
  date_gmt: '2013-07-16 03:02:10 +0000'
  content: "Been a while since the post but agree with the above. A new card for each
    commit would not be useful for me at least. We will review entire issues, stories
    or features, not every commit.\r\n\r\nHaven't actually started using trello yet
    but seems awesome so think I and my team will. So posted to show the solution
    that I found (though I'm sure someone here already have). It's to use zapier as
    bridge between trello and github, there is a page here on zapier detailing it:
    https:&#47;&#47;zapier.com&#47;zapbook&#47;github&#47;trello&#47;.\r\n\r\nIt seems
    to work but have not really gotten around to trying it out yet. It is however
    not free unless you use less than 100 tasks a month. Which is possible if you
    only sync the issues themselves and nothing else. If you however also want to
    sync each commit as a comment to each issue I figure that even smaller teams like
    mine can easily exceed 100 tasks.\r\n\r\nWhat I still don't know however is how
    likely it is for the Zapier bridge to break from changes in the Git or Trello
    API.\r\n\r\nIf anyone knows more I'd love to know. Might post again if I get wiser
    myself."
- id: 12204
  author: Stephen
  author_email: stephen@tailwindapp.com
  author_url: ''
  date: '2014-11-06 18:43:20 +0000'
  date_gmt: '2014-11-06 17:43:20 +0000'
  content: We're looking at Huboard.com which is specifically built with Github issues
    in mind and has a Trello-ish interface
---
<p>After working with git for more then 2 years, few months ago I decided to start using <a href="http:&#47;&#47;www.github.com" target="_blank">Github<&#47;a> to store my repos and test different workflow arrangements. It worked out great, I'm really happy with all it offers (it is a little bit pricy for my taste though) and I'm loving it.</p>
<p>In admin section of my repos some time ago I noticed unfamiliar term called 'Service Hooks' and decided to explore it. Service hooks are already prepared git post receive hooks for integration with other popular web services (<a href="https:&#47;&#47;help.github.com&#47;articles&#47;post-receive-hooks" target="_blank">description<&#47;a>) . Since I use <a href="https:&#47;&#47;trello.com&#47;" target="_blank">Trello<&#47;a> for todo's on some of my pet projects I decided to connect this two webservices.</p>
<p>For easier demonstration I opened a new <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;testing-trello-integration&#47;" target="_blank">github repo<&#47;a>, <a href="https:&#47;&#47;trello.com&#47;board&#47;testing-trello-github-integration&#47;5083d2888fb535b871008eb2" target="_blank">Trello board<&#47;a> and connected them.</p>
<p><img alt="Trello board for testing integration" src="http:&#47;&#47;www.mirosvrtan.me&#47;blog&#47;wp-content&#47;uploads&#47;2012&#47;10&#47;trello-board-for-testing-integration-with-github.png" width="500px" &#47;></p>
<p><img alt="github project for testing trello integration" src="http:&#47;&#47;www.mirosvrtan.me&#47;blog&#47;wp-content&#47;uploads&#47;2012&#47;10&#47;github-project-for-testing-trello-integration.png"  width="500px" &#47;></p>
<p>Now every new commit on master branch is shown in list 'Commits on master' and new pull requests in 'Pull requests'. It is really simple but effective way of tracking stuff to do on smaller projects, I hope to be able to test it very soon in a little bit larger environment though.</p>
<p>It is really easy to setup, after allowing github to access your Trello account via token you can add new pull requests cards to different board then commit cards. It also features ignoring some commits from creation by tracking only master branch or by setting up regular expressions.</p>
<p><img alt="Trello service hook form on github" src="http:&#47;&#47;www.mirosvrtan.me&#47;blog&#47;wp-content&#47;uploads&#47;2012&#47;10&#47;Screenshot.png" width="300px" &#47;></p>
<p><em>Short guide with 4 steps is located under the form (not shown on screenshot here).<&#47;em></p>
<p>One crucial thing missing here is integration of issues. It would be very helpful if issues could be sent too but this is something I'm currently testing with <a href="https:&#47;&#47;zapier.com&#47;" target="_blank">Zapier<&#47;a> (and much more but this will be subject for one of next posts :).</p>
<p>Feel free to fork repository &amp; generate pull requests, this repository and board are used only for demonstration purposes!</p>
