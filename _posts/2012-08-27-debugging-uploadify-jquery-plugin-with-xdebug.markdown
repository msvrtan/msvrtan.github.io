---
layout: post
status: publish
published: true
title: Debugging Uploadify jQuery plugin with XDebug
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 145
wordpress_url: https://www.mirosvrtan.me/blog/?p=145
date: '2012-08-27 19:40:13 +0000'
date_gmt: '2012-08-27 19:40:13 +0000'
categories:
- php
tags:
- php
- xdebug
- uploadify
comments: []
permalink: /blog/2012/08/debugging-uploadify-jquery-plugin-with-xdebug/
---
<p>If you ever decided to use <a href="http://www.uploadify.com" target="_blank"> Uploadify </a> jQuery plug-in you might have noticed problems with debugging remote PHP code that this plugin relies on. We all usually do our web development in Firefox ( <a href="https://addons.mozilla.org/en-us/firefox/addon/firebug/" target="_blank"> Firebug </a> rules! ) we started to use <a href="https://addons.mozilla.org/en-us/firefox/addon/easy-xdebug/" target="_blank"> Easy xdebug </a> plug-in to easily turn on/off xdebug. This plug-in works by setting cookies for current domain, you can turn it on/off quickly (it is located in bottom right corner) so every request to PHP source while this plug-in is turned on will start a new xdebug session. Great tool for fast debugging of server side code!</p>
<p>Unfortunately setting this up will not work with Uploadify Flash version since calls to remote server side is not done inside browser but inside flash plugin. This is sometimes a nightmare because adding new features or bug fixing some edge cases is a nightmare. You can help yourself by building another form that will use same API but it takes time and energy.</p>
<p>Few months ago I found my self blindly debugging it again and remembered that I read somewhere that xdebug parameters can be sent via GET/POST too. All you have to use is <strong>scriptData</strong> element and add XDEBUG_SESSION_START &amp; XDEBUG_SESSION parameters with values that you used when setting up your favourite IDE.</p>
<p>To show you how easy it is I will use sample code from this <a href="http://www.uploadify.com/demos/" target="_blank"> demo </a>:</p>
<pre lang="javascipt">
$(function() {<br />
        $("#file_upload_1").uploadify({<br />
                height        : 30,<br />
                swf           : '/uploadify/uploadify.swf',<br />
                uploader      : '/uploadify/uploadify.php',<br />
                width         : 120<br />
        });<br />
});</pre><br />
All you have to add is scriptData param:</p>
<pre lang="javascipt">
$(function() {<br />
        $("#file_upload_1").uploadify({<br />
                height        : 30,<br />
                swf           : '/uploadify/uploadify.swf',<br />
                uploader      : '/uploadify/uploadify.php',<br />
                width         : 120,<br />
                scriptData    : {<br />
                               'XDEBUG_SESSION_START': 'default' ,<br />
                               'XDEBUG_SESSION': 'default'<br />
                               }<br />
        });<br />
});</pre><br />
Heureka! My xdebug session works!</p>
<p>** <strong>Dont forget to use values you used in your IDE!</strong> **</p>
<p>Before trying this I was playing around with adding this to $_REQUEST, $_POST &amp; $_COOKIE on the beginning of the code but for some reason this doesn't work. Maybe xdebug expects to see this before code starts running but I'm not sure. I hope I helped someone and don't forget not to commit this code into your repository (It can open a whole new can of problems :)).</p>
