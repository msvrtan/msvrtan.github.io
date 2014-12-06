---
layout: post
status: publish
published: true
title: PHP Fatal errors into exceptions natively
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 140
wordpress_url: https://www.mirosvrtan.me/blog/?p=140
date: '2012-08-25 20:12:18 +0000'
date_gmt: '2012-08-25 20:12:18 +0000'
categories:
- php
tags:
- php
- fatal error
- exception
comments: []
permalink: /blog/2012/08/php-fatal-errors-into-exceptions-natively/
---
<p>In my last <a href="https://www.mirosvrtan.me/blog/2012/08/catching-calls-to-undefined-methods-in-php-is-it-a-good-idea/" target="_blank"> blog post </a> I was writing about fatal error problems when undefined methods do occur. I decided to wait with implementation to see what will other developers say and I was surpised a bit with how much people disagreed with the idea. Tthank you all for feedback here, on twitter and reddit since this got me thinking a little bit more. </p>
<p>If you concept your OO classes on public properties vs. getters/setters your PHP code behaves totally different. Lets say you want to load user 79 and print out a welcome message:</p>
<p>Using getter method that is not implemented will get you fatal error saying how undefined method is called and request will stop.</p>
<pre lang="php">
<p>// Instantiate class.<br />
$objUser = new User();<br />
// Load user.<br />
$objUser->load( 79 );<br />
// Print out username<br />
echo 'Hello ' . $objUser->getName() . '!';</p>
<p></pre></p>
<p>On the other hand if you would use public property all you would get is a notice saying how this property does not exist and rest of request would be completed.</p>
<pre lang="php">
<p>// Instantiate class.<br />
$objUser = new User();<br />
// Load user.<br />
$objUser->load( 79 );<br />
// Print out username<br />
echo 'Hello ' . $objUser->name . '!';</p>
<p></pre></p>
<p>I know that this is due to dynamic typing behavior of PHP and no I am not suggesting raising a notice if undefined method gets called but since 5.1.0 there is a <a href="http://php.net/manual/en/class.badmethodcallexception.php" target="_blank"> BadMethodCallException </a> class which would be perfect for this situations. Since I'm not the first one coming with this idea I found a few reports on <a href="https://bugs.php.net/" target="_blank"> PHP bug tracker </a> that were closed due to this not being a bug. Since I don't want to spam bug tracker with a copy of already reported and closed issues I was wondering should one of next PHP versions support this as a feature? </p>
<p>If you like the idea please leave a small comment here and if there would be enough interest we could suggest it at <a href="https://wiki.php.net/rfc" target="_blank"> PHP RFC Wiki </a>. There are already few similar RFCs but they are not regulating fatal errors (<a href="https://wiki.php.net/rfc/errors_as_exceptions" target="_blank"> example </a>).</p>
