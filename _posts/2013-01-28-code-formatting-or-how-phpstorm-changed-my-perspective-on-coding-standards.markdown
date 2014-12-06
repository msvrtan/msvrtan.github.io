---
layout: post
status: publish
published: true
title: Code formatting or how PHPStorm changed my perspective on coding standards
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 353
wordpress_url: http://www.mirosvrtan.me/blog/?p=353
date: '2013-01-28 22:19:11 +0000'
date_gmt: '2013-01-28 21:19:11 +0000'
categories:
- php
tags:
- php
- phpstorm
- IDE
- coding standards
- psr1
- psr2
comments:
- id: 3495
  author: Rasmus Schultz
  author_email: rasmus@mindplay.dk
  author_url: ''
  date: '2013-01-29 14:42:54 +0000'
  date_gmt: '2013-01-29 13:42:54 +0000'
  content: '"Do I like every PSR1&#47;2 fact? No, but really I don&rsquo;t care" -
    I''m glad to hear I''m not the only one who feels this way. People spend way too
    much time obsessing about coding standards. Really, style should be the least
    of our concerns, with tools available to change the style so rapidly. We have
    much bigger things to worry about :-)'
- id: 3496
  author: S&eacute;bastien Lavoie
  author_email: sebastien@lavoie.sl
  author_url: ''
  date: '2013-01-29 15:09:45 +0000'
  date_gmt: '2013-01-29 14:09:45 +0000'
  content: "I generally don&rsquo;t like to use IDE, except when I need to inspect
    or refactor a big portion of a big project. Using text editors feels much more
    powerful, boot time is instant, editing commands is highly tweaked and it will
    be the same software for all the languages you code in.\r\n\r\nThat being said,
    Fabien Potencier (creator of Symfony) had made a little tool that format code
    againt PSR1&#47;2. Simply add it as a pre-commit hook and it's a done deal. https:&#47;&#47;github.com&#47;fabpot&#47;PHP-CS-Fixer"
- id: 3497
  author: Matt
  author_email: a@a.com
  author_url: ''
  date: '2013-01-29 15:45:35 +0000'
  date_gmt: '2013-01-29 14:45:35 +0000'
  content: Netbean's PHP formatter has quite few a options IIRC, and it's completely
    free and cross-platform.
- id: 3501
  author: baspzinga
  author_email: maol@mailinator.com
  author_url: ''
  date: '2013-01-29 18:31:23 +0000'
  date_gmt: '2013-01-29 17:31:23 +0000'
  content: good god please invest in a spell checker
- id: 3504
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2013-01-29 19:23:37 +0000'
  date_gmt: '2013-01-29 18:23:37 +0000'
  content: Tnx Baspzinga, by mistake I forgot to check my spelling.  Now I updated
    post so it should be much better :)
- id: 3505
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2013-01-29 19:29:25 +0000'
  date_gmt: '2013-01-29 18:29:25 +0000'
  content: "What editor do you use? \r\n\r\nBTW, I used Sebastians CS fixer as a test
    on one project, if I remember correctly problem I encountered was that is changes
    all class method names into StudlyCaps, so I got whole bunch of broke calls to
    external libraries :("
- id: 3520
  author: Sebastien Lavoie
  author_email: sebastien@lavoie.sl
  author_url: ''
  date: '2013-01-30 03:48:53 +0000'
  date_gmt: '2013-01-30 02:48:53 +0000'
  content: I use Sublime Text, but TextMate or Notepad++ would do the trick just as
    fine, that&rsquo;s the beauty of it. As for the CS fixer, it only wrecks your
    code if you activate all features, all levels, it has some more conservative modes.
- id: 3547
  author: Jason
  author_email: jason-yang@live.ca
  author_url: ''
  date: '2013-01-30 18:33:22 +0000'
  date_gmt: '2013-01-30 17:33:22 +0000'
  content: "Standards are there mainly for the opensource community, it doesn't hurt
    to use it in a team-based environment too.\r\n\r\nAs for indenting, I am a firm
    believer of both tabs and whitespaces ;)\r\n\r\nUse tab to indent, then spaces
    to position them nicely. Any decent editor will be able to alter the tab's visible
    size, and the fine tuning can be done by spaces, which is the same for all editors.
    Another cool thing about PHPStorm is that it can do this automatically! Just go
    to Settings > Project Settings > PHP (or whatever code type, e.g. css, javascript...etc)
    > Tabs and Indents > Smart tabs (check it)\r\n\r\nI love PHPStorm as well, however
    I am still a little hesitant on buying the license (on the last bit of my evaluation),
    since it's only for 1 year of updates, whereas Netbeans is free (not even going
    to consider Eclipse, it's way too slow) and the newest RC of version 7.3 looks
    promising, and is closing the gap with PHPStorm in terms of speed and standard
    features.\r\n\r\nAnother thing with IDEs (some advanced text editors do it too)
    is that they can automatically detect and match braces&#47;tags, and gives you
    visual clues to them, some even allow collapsing braces and tags, I use that feature
    to check that my braces and tags are closed correctly, although that rarely happens
    now since I create braces and tags in their opening and closing pairs all the
    time now (which some IDEs also auto generate for you)"
- id: 3982
  author: Dejan
  author_email: stojimirovic.dejan@gmail.com
  author_url: ''
  date: '2013-02-26 12:32:16 +0000'
  date_gmt: '2013-02-26 11:32:16 +0000'
  content: "+1 for NetBeans. It's very good IDE for php, css, js, Smarty, twig,..."
- id: 4928
  author: Danko
  author_email: dubajicd@gmail.com
  author_url: ''
  date: '2013-07-11 11:10:57 +0000'
  date_gmt: '2013-07-11 10:10:57 +0000'
  content: "Was using Zend for a while but it was an overkill for the things I do.\r\nThen
    switched to Netbeans php 6.8 because it was good on both Win, Mac and Linux because
    I use all 3 of operating systems. But then 6.9 came out it was even better, but
    then 7.0 screw everything up, 7.1 even worse and I didn't want to bother with
    it after that.\r\nAbout 4-5 months ago I started using PHPStorm and so far I really
    like it, also runs all systems but much much faster. There are few things that
    I don't like here and there but overall great tool.\r\n\r\nThis was a nice read.
    I usually never leave comments, but with site design I couldn't resist :-)\r\n\r\nKeep
    the good work, Danko Dubajic, ThemesKingdom"
- id: 11937
  author: Christian Louboutin Sale
  author_email: fkycnuhgjrs@gmail.com
  author_url: ''
  date: '2014-10-17 12:01:26 +0000'
  date_gmt: '2014-10-17 11:01:26 +0000'
  content: "Valuable info. Lucky me I found your website unintentionally, and I am
    surprised why this coincidence did not took place earlier! I bookmarked it.\r\nChristian
    Louboutin Sale http:&#47;&#47;vi.sualize.us&#47;christian_altadama_140mm_peep_toe_pumps_pink_factory_sale_store_shoes_christian_louboutin_style_fashion_picture_KxaT.html"
---
<p>In last 14 years working as a PHP developer I changed few coding standards. Often for better but not always, reinventing that wheel over and over. For the better part of those 14 years I was working as a one-man-band so changing coding standards was not hard but when I started working in team everything changed. Although we had some coding guidelines, everything else was done on per developer basis which made some projects a total mess.</p>
<p>Why? Developer A would use spaces and then developer B would add new features or bug-fixes using tabs as indent which looked all OK on his IDE of choice. Then developer C would come and change something else using spaces again and it all looked ok for him. Then it was my turn, instead of 8 spaces for tab I use 4 and code looked broken. I couldn't match opening and closing brackets properly so I often closed wrong braces, moved else or added if to unknown territory. For years I was using very popular IDE that had no option of reformatting code so I had too use another IDE only for code reformatting when this happened. As this second IDE was too bloated and slow for me code formating was not done if it was not really needed.</p>
<p>One friend recommended a bright new and very powerful IDE called <a href="http:&#47;&#47;www.jetbrains.com&#47;phpstorm&#47;" target="_blank"> PHPStorm <&#47;a> so I decided to try it out. Though this new IDE doesn't support some of the features I got used to I discovered how powerful their code formatting feature was. Soon after I noticed that having any discussion about code formatting was futile. I just didn't care if I was using spaces or tabs, curly braces in-line, number of spaces inside brackets etc as long as I had option to reformat my code after I wrote it and before committing it. Instead of writing my code clean, indented, with 1 space here and no space there, now I was able to focus on writing the code itself, focusing on what code does and not how it looks. This really liberated me!</p>
<p>Why did I share this with you? Well I noticed that lot of people have been unhappy with new PSR1&#47;2 coding standards. Changing habits is always hard, using one coding standard for years and then switching to some other can be hard if you are not using proper tools. Do I like every PSR1&#47;2 fact? No, but really I don't care. And I don't need to care. PSR1&#47;2 have good readability and since I downloaded already prepared code formatter for PSR1&#47;2 I had no problem to write all of my code in this new standard without any context switching in my head.</p>
<p>I noticed that lot of PHP developers are using editors or IDE's without code formatting options. Switching thousands of lines of code manually and forcing your self to learn new coding rules is just too painful. I did it once and never again. I know developers often despise IDE's since they can be bloated or too slow for what they are used to but this is not the case for all of them. Try PHPStorm, it has a 30 day trial, works on Windows, Linux and Mac OS X so there are really no excuses :)</p>
<p>If you know of other IDE's having powerful code formatter please feel free to comment, all feedback is greatly appreciated!</p>
<p>**UPDATE**</p>
<p>Sorry everybody, site is&nbsp;experiencing some internal server problems so it was down few times today. Sorry for that!</p>
<p>&nbsp;</p>
