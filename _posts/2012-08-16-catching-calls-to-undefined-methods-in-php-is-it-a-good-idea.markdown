---
layout: post
status: publish
published: true
title: Catching calls to undefined methods in PHP - is it a good idea?
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 134
wordpress_url: http://www.mirosvrtan.me/blog/?p=134
date: '2012-08-16 21:08:02 +0000'
date_gmt: '2012-08-16 21:08:02 +0000'
categories:
- php
tags:
- php
- errors
- exceptions
comments: []
permalink: /blog/2012/08/catching-calls-to-undefined-methods-in-php-is-it-a-good-idea/
---
<p>Two years ago we built a small class for easier logging and reporting of errors inside our applications by using <a href="http://php.net/manual/en/function.set-error-handler.php" target="_blank">set_error_handler()</a>. We built it cause:</p>
<p>1) In development mode error display can cause problems</p>
<p>We found ourselves in some situations where PHP notices would be shown inside javascript or hidden elements and it was giving us whole bunch of problems. By using our custom error handler we are able to show errors on the bottom of the page.</p>
<p>2) Staging server reporting</p>
<p>On staging servers we needed fast notifications of any errors so we implemented emailing of all errors to developers which enabled us to react much faster when something goes wrong. </p>
<p>3) Production server reporting</p>
<p>On some smaller productions we have enabled email notifications but on larger ones that was not an option so we decided to log those errors into files which we then can easily pull home. Yes Apache can do this for us too but we needed more information on each error.</p>
<p>If you have any experience with set_error_handler() function then you know that it can not catch fatal errors. There is also a solution for catching them with usage of <a href="php.net/manual/en/function.register-shutdown-function.php" target="_blank"> register_shutdown_function() </a> and I will be testing this implementation very soon (not implemented yet). </p>
<p>But what if we can transform some of those fatal errors into exceptions? We already have a lot of catch blocks prepared and although register_shutdown_function() will give us a report about error, it will show user a broken page instead of a nice 500 Server error custom page. Also maybe that fatal error would occur in some part of process that we already have covered with catch blocks and rest of the page would be shown normally. One of most often fatal errors I proudly produce is a call to undefined method in class that was injected as a dependency. </p>
<p>So my idea is to throw exception in __call magic method and those fatal errors will be transformed into something I can work with. Now my main worry is why PHP is not behaving like that already? Am I missing/forgetting something? </p>
<p>Suggestions and comments are welcomed!</p>
