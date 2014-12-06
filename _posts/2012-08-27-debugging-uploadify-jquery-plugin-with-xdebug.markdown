---
layout: post
status: publish
published: true
title: Debugging Uploadify jQuery plugin with XDebug
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 145
wordpress_url: http://www.mirosvrtan.me/blog/?p=145
date: '2012-08-27 19:40:13 +0000'
date_gmt: '2012-08-27 19:40:13 +0000'
categories:
- php
tags:
- php
- xdebug
- uploadify
comments:
- id: 5026
  author: Robertas
  author_email: robertasjasmontas@gmail.com
  author_url: ''
  date: '2013-07-25 10:41:36 +0000'
  date_gmt: '2013-07-25 09:41:36 +0000'
  content: Great post ! You have saved a lot of my time :)
---
<p>If you ever decided to use <a href="http:&#47;&#47;www.uploadify.com" target="_blank"> Uploadify <&#47;a> jQuery plug-in you might have noticed problems with debugging remote PHP code that this plugin relies on. We all usually do our web development in Firefox ( <a href="https:&#47;&#47;addons.mozilla.org&#47;en-us&#47;firefox&#47;addon&#47;firebug&#47;" target="_blank"> Firebug <&#47;a> rules! ) we started to use <a href="https:&#47;&#47;addons.mozilla.org&#47;en-us&#47;firefox&#47;addon&#47;easy-xdebug&#47;" target="_blank"> Easy xdebug <&#47;a> plug-in to easily turn on&#47;off xdebug. This plug-in works by setting cookies for current domain, you can turn it on&#47;off quickly (it is located in bottom right corner) so every request to PHP source while this plug-in is turned on will start a new xdebug session. Great tool for fast debugging of server side code!</p>
<p>Unfortunately setting this up will not work with Uploadify Flash version since calls to remote server side is not done inside browser but inside flash plugin. This is sometimes a nightmare because adding new features or bug fixing some edge cases is a nightmare. You can help yourself by building another form that will use same API but it takes time and energy.</p>
<p>Few months ago I found my self blindly debugging it again and remembered that I read somewhere that xdebug parameters can be sent via GET&#47;POST too. All you have to use is <strong>scriptData<&#47;strong> element and add XDEBUG_SESSION_START &amp; XDEBUG_SESSION parameters with values that you used when setting up your favourite IDE.</p>
<p>To show you how easy it is I will use sample code from this <a href="http:&#47;&#47;www.uploadify.com&#47;demos&#47;" target="_blank"> demo <&#47;a>:</p>
<pre lang="javascipt">
$(function() {<br />
        $("#file_upload_1").uploadify({<br />
                height        : 30,<br />
                swf           : '&#47;uploadify&#47;uploadify.swf',<br />
                uploader      : '&#47;uploadify&#47;uploadify.php',<br />
                width         : 120<br />
        });<br />
});<&#47;pre><br />
All you have to add is scriptData param:</p>
<pre lang="javascipt">
$(function() {<br />
        $("#file_upload_1").uploadify({<br />
                height        : 30,<br />
                swf           : '&#47;uploadify&#47;uploadify.swf',<br />
                uploader      : '&#47;uploadify&#47;uploadify.php',<br />
                width         : 120,<br />
                scriptData    : {<br />
                               'XDEBUG_SESSION_START': 'default' ,<br />
                               'XDEBUG_SESSION': 'default'<br />
                               }<br />
        });<br />
});<&#47;pre><br />
Heureka! My xdebug session works!</p>
<p>** <strong>Dont forget to use values you used in your IDE!<&#47;strong> **</p>
<p>Before trying this I was playing around with adding this to $_REQUEST, $_POST &amp; $_COOKIE on the beginning of the code but for some reason this doesn't work. Maybe xdebug expects to see this before code starts running but I'm not sure. I hope I helped someone and don't forget not to commit this code into your repository (It can open a whole new can of problems :)).</p>
