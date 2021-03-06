---
layout: post
status: publish
published: true
title: Performance of different PHP class implementations
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 47
wordpress_url: https://www.mirosvrtan.me/blog/?p=47
date: '2012-06-26 22:21:05 +0000'
date_gmt: '2012-06-26 22:21:05 +0000'
categories:
- php
tags:
- php
- optimization
- performance
comments: []
permalink: /blog/2012/06/performance-of-different-php-class-implementations/
---
<h2>Introduction</h2><br />
There are few types of class implementations used in PHP and I wanted to see how will they effect performance on such a low level.</p>
<p>Here is a short list of what I was testing:</p>
<ol>
<li>Class implementing public properties</li>
<li>Class implementing protected properties with usage of magic __get/__set methods to access properties</li>
<li>Class implementing protected properties with usage of magic __get/__set methods to access properties with checking if this property really exists</li>
<li>Class implementing protected properties with usage of getters and setters</li>
<li>Class implementing protected properties (which are not PHP types but simple classes) with usage of getters and setters</li><br />
</ol><br />
All tests supported:</p>
<ul>
<li>X iterations</li>
<li>showing memory usage</li>
<li>showing peak memory usage</li>
<li>showing time used</li><br />
</ul><br />
There were 3 tests generated</p>
<ol>
<li>Object initialization</li>
<li>Object load</li>
<li>Object load with pushing objects into array instead of destroying them</li><br />
</ol></p>
<h2>Testing</h2><br />
<strong>1 Object initialization</strong></p>
<p>Idea here was to iterate 10000 object creation to see if there is any difference in instantiating classes with 1 method vs few methods so later tests would not be polluted.</p>
<p>All tests but the last one were same, and the last one was 5x slower since there was a need to instantiate additional classes as properties inside object.</p>
<p><em>Test 1: using directly properties</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.2849521636963 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 2: using magic __set</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.3259601593018 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 3: using magic __set with checking if property exists</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.3290596008301 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 4: using implemented setters</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.335973739624 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 5</em>: using objects for properties<br />
Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 31.872987747192 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p>&nbsp;</p>
<p><strong>2 Object load</strong></p>
<p>Iterating through creation of 10000 objects, after each object was instantiated, load() method was called with array holding 5 property names and values. Each of the property values was filled using respective methods ( directly accessing property or given setters)</p>
<p><em>Test 1: using directly properties</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 25.489807128906 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 2: using magic __set<br />
</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 86.797952651978 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 3: using magic __set with checking if property exists<br />
</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 136.67583465576 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 4: using implemented setters</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 71.701049804688 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p><em>Test 5</em>: using objects for properties</p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 146.02208137512 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p>I was expecting that magic methods or setters would be somewhat slower then directly accessing public properties but this is really too much. More details later.</p>
<p><strong>3 Object load with pushing objects into array instead of destroying them</strong></p>
<p>Testing method was same as test #2 but I added pushing objects into array after loading so I could test how memory is behaving when garbage collection is not able to destroy them.</p>
<p><em>Test 1: using directly properties</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 28.702974319458 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B</p>
<p><em>Test 2: using magic __set</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 89.023113250732 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B</p>
<p><em>Test 3: using magic __set with checking if property exists</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 147.24612236023 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B</p>
<p><em>Test 4: using implemented setters</em></p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 75.994968414307 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2,359,296 B</p>
<p><em>Test 5</em>: using objects for properties</p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 155.48205375671 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 7,340,032 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 7,340,032 B</p>
<p>First 4 tests are using same amount of memory, but I actually hoped to see some difference since classes are different. Fifth test is expectedly using 3x more memory because of extra 50k simple objects representing object properties.</p>
<h2>Consclusion:</h2><br />
If you look into differences on 2nd test for cases #1, #2 and #4 you will see that calling load method on public properties took 19ms, on magic methods 80ms and 65ms on implemented getters and setters. From this I can see that calling a method to set a property value is 200% slower (#1 vs #4 ) while calling a magic method adds addiditonal 23% (#4 vs #2).</p>
<p>I expected magic methods to be somewhat slower but I didn't expect simple setters to be 300% slower then accessing directly properties. So I did one additional test with only calling load method (but load method is doing nothing!) and I got</p>
<p>Time spent:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 15.813827514648 ms<br />
Memory start:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory end:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B<br />
Memory peak:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 262,144 B</p>
<p>This tells me that 10k of calls to load method is taking 9ms. So setting 50k properties through direct property access takes ~3ms and accessing 50k setter methods takes ~70ms.</p>
<p>I was&nbsp;surprised to see such a big difference (23x times slower!!). Using properties directly might seem like a micro optimization but as PHP has moved towards object oriented paradigm, accessing properties is a very common operation so loosing performance here could make a lot of difference.</p>
<p>In the next post I will cover what was the idea of fifth case, in the mean time&nbsp; you can see code for this tests on <a href="https://github.com/OrimFoundation/PhpObjectifyTests" target="_blank">github</a>, feel free to try them (there are bash scripts for easier testing of each one) and feel free to comment.</p>
<p>&nbsp;</p>
