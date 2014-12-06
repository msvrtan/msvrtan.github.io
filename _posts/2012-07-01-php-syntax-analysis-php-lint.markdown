---
layout: post
status: publish
published: true
title: PHP syntax analysis - PHP lint
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 70
wordpress_url: http://www.mirosvrtan.me/blog/?p=70
date: '2012-07-01 17:21:24 +0000'
date_gmt: '2012-07-01 17:21:24 +0000'
categories:
- php
tags:
- php
- testing
- better code
- tools
comments: []
---
<p>&nbsp;</p>
<p>On more then few occasions I found myself committing broken code to our git repository (and deploying it onto staging server) so I started to look into how to minimize chance of doing that. As we are a team of 10 PHP developers working continuosly on multiple projects this is something we desperately need.</p>
<p>First step was probably the easiest: syntax error checking. <a href="http:&#47;&#47;en.wikipedia.org&#47;wiki&#47;Syntax_error">Syntax errors<&#47;a> are easy to fix, don't happen often (if you are actually testing code you are working on locally :) but however they do happen. Also you have to start somewhere :)</p>
<p>The easiest tool to do it in PHP is PHP itself by using -l option:</p>
<p><strong>php -l name_of_file.php<&#47;strong></p>
<p>Unfortunately it doesnt support recursive analysis, so I built a small bash script to do it (I work on Ubuntu Linux):</p>
<p><strong>find application&#47; -name '*.php' -exec php -l {} \; |grep -v 'No syntax error'<&#47;strong></p>
<p>This will look through whole application folder (including subfolders) for all *.php files. It will print only errors, that's why <strong>|grep<&#47;strong> part is needed so it will remove all data about files where no error was found. Output it returns will look like this:</p>
<p><strong>PHP Parse error: syntax error, unexpected '(', expecting ',' or ';' in application&#47;class&#47;balance_sheet_fix.class.php on line 8<&#47;strong><br />
<strong> Errors parsing application&#47;class&#47;balance_sheet_fix.class.php<&#47;strong></p>
<p>Current example was run on codebase for one of projects I work on, codebase has 9Mb and 1629 files and it took around 30 seconds on Intel based i5 desktop. PHP lint proved to be pretty nifty tool, not really meant to be runned after every change in code but you can always run it before commiting your changes and be sure to avoid those really basic bugs.</p>
<p>Hope I helped somebody, my next step was <a href="http:&#47;&#47;pear.php.net&#47;package&#47;PHP_CodeSniffer&#47;redirected">PHP CodeSniffer<&#47;a> and if there will be any interest I can write a short tutorial on why and how. Also I hope to integrate all of code checking into one of those cool CI tools like Jenkins so if you have any suggestions or tips I would be very greatefull.</p>
<p>Update #1: I forgot to mention that this tool will return only first syntax error in file so after fixing it you must run it again to see if that file had more errors.</p>
<p>***<br />
To get number of files use: "find application&#47; -name '*.php' | wc -l"</p>
