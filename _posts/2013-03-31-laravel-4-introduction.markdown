---
layout: post
status: publish
published: true
title: Laravel 4 - introduction
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 386
wordpress_url: http://www.mirosvrtan.me/blog/?p=386
date: '2013-03-31 20:17:29 +0000'
date_gmt: '2013-03-31 19:17:29 +0000'
categories:
- php
tags:
- php
- laravel4
comments: []
permalink: /blog/2013/03/laravel-4-introduction/
---
<p>After years of working in a company using inhouse framework, before switching jobs I decided to expand my knowledge and find a new framework I will base my projects on.</p>
<p>Zend and Yii frameworks were between versions, some older frameworks have been ruled out since I didn't want to use something that supports PHP < 5.3 (this means they don't use features like namespacing). Symfony 2 looked as something I will go with until I've heard lot of great things about Laravel's new version architecture being built using composer and code from other frameworks/libraries. I decided to check it out.</p>
<p>One big difference from Sf2 was that I got my 'Hello world' app running in few minutes while I had some problems with Sf2 setup. Though I started using it while Laravel4 was still in heavy development (November 2012) it was working very well, of course there were things breaking after some updates but this was something I was prepared. Now I'm running few simple applications (none of them are public) on it, and I must say it was a good choice.</p>
<p>Code is very well documented and clean, source code is hosted on github so anybody can contribute. Unit test coverage is good so bugs are really rare. Newbies can use older tutorials to find out how to do something since framework resources for L4 are scarce. Be warned that there were changes in architecture and code is now using PSR1 standard so you will have to figure out some smaller things yourself.</p>
<p>Core of framework is built using other projects code (i.e. Symfony2), composer gives developers power of easy dependency management and easily replacing/adding other libraries to your project. When talking about community built bundles and libraries there are only few but I expect that lot of user code will be available when L4 comes out from beta. Also lot of Sf2 user bundles and libraries should be easily integrated in your L4 based applications.</p>
<p>Lot of things are supported out of box (i.e. database migrations, REST, redis, memcached, etc.), views can be built using PHP or Blade&nbsp;templating engine which uses syntax similar to other engines and supports extending views and using view components. This means that you can easily build master templates or view component and reuse them multiple times. Artisan is CLI tool that is great help for building migrations, boiler code templates and much more.</p>
<p>If you are interested I will have a session on next <a href="http://zgphp.org/2013/03/zgphp-meetup-20-moze-sad-proljetni-meetup/" target="_blank">ZgPHP meetup</a>.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
