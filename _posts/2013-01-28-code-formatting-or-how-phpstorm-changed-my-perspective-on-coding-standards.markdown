---
layout: post
status: publish
published: true
title: Code formatting or how PHPStorm changed my perspective on coding standards
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 353
wordpress_url: https://www.mirosvrtan.me/blog/?p=353
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
comments: []
permalink: /blog/2013/01/code-formatting-or-how-phpstorm-changed-my-perspective-on-coding-standards/

---
<p>In last 14 years working as a PHP developer I changed few coding standards. Often for better but not always, reinventing that wheel over and over. For the better part of those 14 years I was working as a one-man-band so changing coding standards was not hard but when I started working in team everything changed. Although we had some coding guidelines, everything else was done on per developer basis which made some projects a total mess.</p>
<p>Why? Developer A would use spaces and then developer B would add new features or bug-fixes using tabs as indent which looked all OK on his IDE of choice. Then developer C would come and change something else using spaces again and it all looked ok for him. Then it was my turn, instead of 8 spaces for tab I use 4 and code looked broken. I couldn't match opening and closing brackets properly so I often closed wrong braces, moved else or added if to unknown territory. For years I was using very popular IDE that had no option of reformatting code so I had too use another IDE only for code reformatting when this happened. As this second IDE was too bloated and slow for me code formating was not done if it was not really needed.</p>
<p>One friend recommended a bright new and very powerful IDE called <a href="http://www.jetbrains.com/phpstorm/" target="_blank"> PHPStorm </a> so I decided to try it out. Though this new IDE doesn't support some of the features I got used to I discovered how powerful their code formatting feature was. Soon after I noticed that having any discussion about code formatting was futile. I just didn't care if I was using spaces or tabs, curly braces in-line, number of spaces inside brackets etc as long as I had option to reformat my code after I wrote it and before committing it. Instead of writing my code clean, indented, with 1 space here and no space there, now I was able to focus on writing the code itself, focusing on what code does and not how it looks. This really liberated me!</p>
<p>Why did I share this with you? Well I noticed that lot of people have been unhappy with new PSR1/2 coding standards. Changing habits is always hard, using one coding standard for years and then switching to some other can be hard if you are not using proper tools. Do I like every PSR1/2 fact? No, but really I don't care. And I don't need to care. PSR1/2 have good readability and since I downloaded already prepared code formatter for PSR1/2 I had no problem to write all of my code in this new standard without any context switching in my head.</p>
<p>I noticed that lot of PHP developers are using editors or IDE's without code formatting options. Switching thousands of lines of code manually and forcing your self to learn new coding rules is just too painful. I did it once and never again. I know developers often despise IDE's since they can be bloated or too slow for what they are used to but this is not the case for all of them. Try PHPStorm, it has a 30 day trial, works on Windows, Linux and Mac OS X so there are really no excuses :)</p>
<p>If you know of other IDE's having powerful code formatter please feel free to comment, all feedback is greatly appreciated!</p>
<p>**UPDATE**</p>
<p>Sorry everybody, site is&nbsp;experiencing some internal server problems so it was down few times today. Sorry for that!</p>
<p>&nbsp;</p>
