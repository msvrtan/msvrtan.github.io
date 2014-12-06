---
layout: post
status: publish
published: true
title: Singleton pattern in PHP
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 87
wordpress_url: http://www.mirosvrtan.me/blog/?p=87
date: '2012-08-08 23:32:31 +0000'
date_gmt: '2012-08-08 23:32:31 +0000'
categories:
- php
tags:
- php
- design patterns
- intermediate
comments:
- id: 95
  author: damir
  author_email: damir.svrtan@gmail.com
  author_url: ''
  date: '2012-08-10 06:17:23 +0000'
  date_gmt: '2012-08-10 06:17:23 +0000'
  content: isti primjer koji si i meni rekao prije pol godine :)
- id: 97
  author: Milan Popovic
  author_email: komita1981@gmail.com
  author_url: http://www.milanpopovic.me
  date: '2012-08-10 13:32:48 +0000'
  date_gmt: '2012-08-10 13:32:48 +0000'
  content: "There is one more similar pattern known as Multiton. Multiton adds named
    instances to singleton. In your example that would be\r\n\r\n<pre>\r\nclass SessionMultiton\r\n{\r\n
    \r\n    protected static $instances;\r\n \r\n    protected function __construct()\r\n
    \   {\r\n    }\r\n \r\n    public static function getInstance($instance = null)\r\n
    \   {\r\n\t\tif (\\array_key_exists($instance, static::$instances))\r\n\t\t{\r\n\t\t\treturn
    static::$instances[$instance];\r\n\t\t}\r\n\t\tstatic::$instances[$instance] =
    new static();\r\n\t\treturn static::$instances[$instance];\r\n    }\r\n \r\n}\r\n<&#47;pre>"
- id: 103
  author: tere&scaron;ko
  author_email: martins.teresko@gmail.com
  author_url: ''
  date: '2012-08-15 07:26:32 +0000'
  date_gmt: '2012-08-15 07:26:32 +0000'
  content: Another stupid article from people  who, instead of learning object oriented
    programming and dependency injections, decide "oh , i will just use global state
    here". Congratulation of popularizing the use of anti-patterns,
---
<p>Why singleton? Idea is to limit number of instances of a desired class, you don't want to have 4 connections to your DB server or 3 instances of session. First one you can but you dont want to do since resources are usually very limited and second one can create bunch of problems in logic.</p>
<p>In the good old days (actually older versions of PHP), developers used global variables to achieve this but that instantiated whole bunch of new problems. So how to do this?</p>
<p>I decided to create a simple session singleton class (this code here is stripped down only to show singleton related logic, the whole class can be found <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonSimple&#47;Session.singleton.php" target="_blank">here<&#47;a>):</p>
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
<&#47;pre></p>
<p><strong>Key singleton features<&#47;strong>:</p>
<p>1) Constructor is marked as protected so any instantiation would cause a fatal error: "PHP Fatal error:&nbsp; Call to protected SessionSingleton::__construct() from invalid context in .."</p>
<pre lang="php" line="1">
$obj = new SessionSingleton();<br />
<&#47;pre></p>
<p>2) Method getInstance() is here to instantiate SessionSingleton class only on first call and return already instantiated object every other time. Here is proper way to get object:</p>
<pre lang="php" line="1">
$obj = SessionSingleton::getInstance();<br />
<&#47;pre></p>
<p>3) Static instance property is a placeholder where single instance of SessionSingleton will be 'saved' for future reuse and it is marked protected so no outside code could for instance delete it.</p>
<p>I've created a <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonSimple&#47;index.php" target="_blank">short script<&#47;a> where you can see how multiple calls to SessionSingleton::getInstance() behave. There you can see that changing property in one of them will influence other one since both variables use same object instance.</p>
