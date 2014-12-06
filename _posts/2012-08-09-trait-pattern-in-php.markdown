---
layout: post
status: publish
published: true
title: Trait pattern in PHP
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 103
wordpress_url: http://www.mirosvrtan.me/blog/?p=103
date: '2012-08-09 21:48:38 +0000'
date_gmt: '2012-08-09 21:48:38 +0000'
categories:
- php
tags:
- php
- design patterns
- intermediate
comments: []
---
<h1>Trait pattern description<&#47;h1><br />
Instead of trying to explain traits myself I will use PHP manual and wikipedia descriptions:</p>
<p><a href="http:&#47;&#47;en.wikipedia.org&#47;wiki&#47;Trait_%28computer_programming%29" target="_blank">Wikipedia<&#47;a>:</p>
<p><em>In computer programming, a trait is a collection of methods, used as a "simple conceptual model for structuring object oriented programs"<&#47;em></p>
<p><a href="http:&#47;&#47;php.net&#47;manual&#47;en&#47;language.oop5.traits.php" target="_blank">PHP manual<&#47;a>:</p>
<p><em>"A Trait is similar to a class, but only intended to group functionality in a fine-grained and consistent way. It is not possible to instantiate a Trait on its own. It is an addition to traditional inheritance and enables horizontal composition of behavior; that is, the application of class members without requiring inheritance. "<&#47;em></p>
<h1>SessionSingleton example<&#47;h1><br />
I wrote a short <a href="http:&#47;&#47;www.mirosvrtan.me&#47;blog&#47;2012&#47;08&#47;singleton-pattern-in-php&#47;" target="_blank">blog post<&#47;a> on singleton pattern and will use SessionSingleton example here to describe why we needed traits so badly (they are one of features that came with PHP 5.4).</p>
<p>As you can see in <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonSimple&#47;Session.singleton.php" target="_blank"> SessionSingleton class <&#47;a> there are ~10 lines of code (without comments) needed for implementing Singleton pattern so why would we copy them around every time we want to build a singleton class? Lets move those lines of code into <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonExtended&#47;Base.singleton.php" target="_blank"> separate class <&#47;a> that all singleton classes will extend. This means that our <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonExtended&#47;Session.singleton.php" target="_blank"> SessionSingleton class <&#47;a> is now somewhat cleaner and easier to maintain since any bugs detected on Singleton implementation can be fixed on one place instead of using search-and-destroy bugfixing.</p>
<h1>The next step .. traits<&#47;h1><br />
As you can see now we still have get(),set() &amp; add() methods defined that are probably used all around already and are being copyed back and forth. We shouldnt move it into base singleton class since all other singletons will not have any use of it and on the other hand if we want some other classes to use it we would give them Singleton availability which we dont want. Since PHP doesn't support multiple inheritance or mixins we have 2 solutions:</p>
<p>1) Copy paste them around, which is boooring :)<br />
2) Use traits</p>
<p>So we have moved <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonTraits&#47;Singleton.trait.php" target="_blank"> Singleton <&#47;a> and <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonTraits&#47;Values.trait.php" target="_blank"> Values <&#47;a> (this is how I decided to call those pesky get,set and add methods collection) into their respective traits. New <a href="https:&#47;&#47;github.com&#47;msvrtan&#47;xmpl&#47;blob&#47;master&#47;SingletonTraits&#47;Session.singleton.php" target="_blank"> session singleton class <&#47;a> now implements only actual logic needed, setting up $_SESSION data into $arrValues and looks like this:</p>
<pre lang="php">class SessionSingleton<br />
{</p>
<p>    use SingletonTrait, ValuesTrait;</p>
<p>    protected function __construct()<br />
    {</p>
<p>        $this->arrValues = $_SESSION;<br />
    }<br />
}<&#47;pre><br />
This way we can do <a href="http:&#47;&#47;en.wikipedia.org&#47;wiki&#47;Don%27t_repeat_yourself" target="_blank"> DRY <&#47;a> much easier which will help us make better code (all of those copy pasting usually produces forgetting something, copying unwanted or not needed parts of code), easier to maintain (bugfix in implementation can be fixed on one place) and help us build new features with much less pain.</p>
<p><strong>NOTE<&#47;strong>: this code is only an example of implementation for session singleton used only for explaining singleton and trait patterns.</p>
