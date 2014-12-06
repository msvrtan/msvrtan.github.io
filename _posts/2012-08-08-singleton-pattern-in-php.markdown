---
layout: post
status: publish
published: true
title: Singleton pattern in PHP
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 87
wordpress_url: https://www.mirosvrtan.me/blog/?p=87
date: '2012-08-08 23:32:31 +0000'
date_gmt: '2012-08-08 23:32:31 +0000'
categories:
- php
tags:
- php
- design patterns
- intermediate
comments: []
permalink: /blog/2012/08/singleton-pattern-in-php/
---
<p>Why singleton? Idea is to limit number of instances of a desired class, you don't want to have 4 connections to your DB server or 3 instances of session. First one you can but you dont want to do since resources are usually very limited and second one can create bunch of problems in logic.</p>
<p>In the good old days (actually older versions of PHP), developers used global variables to achieve this but that instantiated whole bunch of new problems. So how to do this?</p>
<p>I decided to create a simple session singleton class (this code here is stripped down only to show singleton related logic, the whole class can be found <a href="https://github.com/msvrtan/xmpl/blob/master/SingletonSimple/Session.singleton.php" target="_blank">here</a>):</p>
<pre lang="php" line="1">
<p>class SessionSingleton<br />
{</p>
<p>    protected static $instance;</p>
<p>    protected function __construct()<br />
    {<br />
    }</p>
<p>    public static function getInstance()<br />
    {</p>
<p>        if (static::$instance === null) {<br />
            static::$instance = new static();<br />
        }</p>
<p>        return static::$instance;<br />
    }</p>
<p>}<br />
</pre></p>
<p><strong>Key singleton features</strong>:</p>
<p>1) Constructor is marked as protected so any instantiation would cause a fatal error: "PHP Fatal error:&nbsp; Call to protected SessionSingleton::__construct() from invalid context in .."</p>
<pre lang="php" line="1">
$obj = new SessionSingleton();<br />
</pre></p>
<p>2) Method getInstance() is here to instantiate SessionSingleton class only on first call and return already instantiated object every other time. Here is proper way to get object:</p>
<pre lang="php" line="1">
$obj = SessionSingleton::getInstance();<br />
</pre></p>
<p>3) Static instance property is a placeholder where single instance of SessionSingleton will be 'saved' for future reuse and it is marked protected so no outside code could for instance delete it.</p>
<p>I've created a <a href="https://github.com/msvrtan/xmpl/blob/master/SingletonSimple/index.php" target="_blank">short script</a> where you can see how multiple calls to SessionSingleton::getInstance() behave. There you can see that changing property in one of them will influence other one since both variables use same object instance.</p>
