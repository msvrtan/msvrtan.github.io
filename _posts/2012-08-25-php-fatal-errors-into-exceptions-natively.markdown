---
layout: post
status: publish
published: true
title: PHP Fatal errors into exceptions natively
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 140
wordpress_url: http://www.mirosvrtan.me/blog/?p=140
date: '2012-08-25 20:12:18 +0000'
date_gmt: '2012-08-25 20:12:18 +0000'
categories:
- php
tags:
- php
- fatal error
- exception
comments:
- id: 169
  author: Atachi
  author_email: atachi.hayashime@gmail.com
  author_url: ''
  date: '2012-08-29 07:44:21 +0000'
  date_gmt: '2012-08-29 07:44:21 +0000'
  content: "While PHP needs better error handling, making everything an exception
    should not be the solution.\r\n\r\nExceptions should only be thrown by run time
    errors, not compile time errors.\r\nA missing method on a class is compile time
    - except when using dynamic classes (there reflection can perhaps throw an exception).\r\n\r\nTHe
    problem with this perception is, that PHP is too dynamic in that regard. It shouldn't
    actually give any existing output if there is a compile error somewhere as it
    leads to this idea that \"I want to catch fatal errors and continue from there\".\r\nIf
    you need to actually continue after a fatal error, you should rework your architecture
    to prevent it from even happening.\r\n\r\nAt least that is my opinion - and that
    of several other programming languages."
- id: 184
  author: mario
  author_email: no@dodgeit.com
  author_url: ''
  date: '2012-08-30 14:18:22 +0000'
  date_gmt: '2012-08-30 14:18:22 +0000'
  content: "I'm confused about the use case here. If you call an undeclared method,
    you get a fatal error.\r\n\r\nWhy would you want en exception here? Exceptions
    are for errors that may occur at runtime. Undeclared methods are something that
    occurs and should be effing fixed at the development stage. If you can't get it
    fixed until deployment, I'm not sure an assortment of exceptions raises the code
    quality measurably."
- id: 4606
  author: Patrick
  author_email: pkolenic@gmail.com
  author_url: ''
  date: '2013-06-04 20:09:48 +0000'
  date_gmt: '2013-06-04 19:09:48 +0000'
  content: "While I agree that missing methods should be addressed in the development
    stage, there are times when it would be useful to catch the fatal error.\r\n\r\nHere
    is an example:  Our site's production configuration does not display the Fatal
    Error.   If an error occurs, an error page is displayed for a period of time and
    then the user is redirected to the Front Page of the Site.  However if the Fatal
    Error occurs on the front page, then the browser's default error page shows, (except
    Firefox which only shows a white page).\r\n\r\nNow the Fatal Error will be show
    in the development environment, but what happens if a new deployment to the Production
    Servers happens to fail to deploy a file that has a new function in it?  On our
    production site we have to isolate all the changes in the controller file that
    is not working and then isolate which support file failed to deploy.\r\n\r\nIf
    on the other hand we were able to catch the Fatal Error and write it to a log
    file, then looking at the log file would quickly identify what failed to be deployed."
- id: 5032
  author: David
  author_email: dsoussan@gmail.com
  author_url: ''
  date: '2013-07-26 09:11:30 +0000'
  date_gmt: '2013-07-26 08:11:30 +0000'
  content: 'I''m currently writing a public API which immediately opens up this issue
    of undeclared methods: user simply makes a bad api call. So I have to guard against
    it by running method_exists and&#47;or is_callable for every request, %99.9999
    of which I expect to be correct. So that is my use case for being able to turn
    fatal errors into catchable exceptions which can be handled gracefully. I''m sure
    there are many others.'
---
<p>In my last <a href="http:&#47;&#47;www.mirosvrtan.me&#47;blog&#47;2012&#47;08&#47;catching-calls-to-undefined-methods-in-php-is-it-a-good-idea&#47;" target="_blank"> blog post <&#47;a> I was writing about fatal error problems when undefined methods do occur. I decided to wait with implementation to see what will other developers say and I was surpised a bit with how much people disagreed with the idea. Tthank you all for feedback here, on twitter and reddit since this got me thinking a little bit more. </p>
<p>If you concept your OO classes on public properties vs. getters&#47;setters your PHP code behaves totally different. Lets say you want to load user 79 and print out a welcome message:</p>
<p>Using getter method that is not implemented will get you fatal error saying how undefined method is called and request will stop.</p>
<pre lang="php">
<p>&#47;&#47; Instantiate class.<br />
$objUser = new User();<br />
&#47;&#47; Load user.<br />
$objUser->load( 79 );<br />
&#47;&#47; Print out username<br />
echo 'Hello ' . $objUser->getName() . '!';</p>
<p><&#47;pre></p>
<p>On the other hand if you would use public property all you would get is a notice saying how this property does not exist and rest of request would be completed.</p>
<pre lang="php">
<p>&#47;&#47; Instantiate class.<br />
$objUser = new User();<br />
&#47;&#47; Load user.<br />
$objUser->load( 79 );<br />
&#47;&#47; Print out username<br />
echo 'Hello ' . $objUser->name . '!';</p>
<p><&#47;pre></p>
<p>I know that this is due to dynamic typing behavior of PHP and no I am not suggesting raising a notice if undefined method gets called but since 5.1.0 there is a <a href="http:&#47;&#47;php.net&#47;manual&#47;en&#47;class.badmethodcallexception.php" target="_blank"> BadMethodCallException <&#47;a> class which would be perfect for this situations. Since I'm not the first one coming with this idea I found a few reports on <a href="https:&#47;&#47;bugs.php.net&#47;" target="_blank"> PHP bug tracker <&#47;a> that were closed due to this not being a bug. Since I don't want to spam bug tracker with a copy of already reported and closed issues I was wondering should one of next PHP versions support this as a feature? </p>
<p>If you like the idea please leave a small comment here and if there would be enough interest we could suggest it at <a href="https:&#47;&#47;wiki.php.net&#47;rfc" target="_blank"> PHP RFC Wiki <&#47;a>. There are already few similar RFCs but they are not regulating fatal errors (<a href="https:&#47;&#47;wiki.php.net&#47;rfc&#47;errors_as_exceptions" target="_blank"> example <&#47;a>).</p>
