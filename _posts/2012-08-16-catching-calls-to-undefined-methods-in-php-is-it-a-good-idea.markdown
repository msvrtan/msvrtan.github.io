---
layout: post
status: publish
published: true
title: Catching calls to undefined methods in PHP - is it a good idea?
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: http://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: http://www.mirosvrtan.me/
wordpress_id: 134
wordpress_url: http://www.mirosvrtan.me/blog/?p=134
date: '2012-08-16 21:08:02 +0000'
date_gmt: '2012-08-16 21:08:02 +0000'
categories:
- php
tags:
- php
- errors
- exceptions
comments:
- id: 107
  author: Ivan Hu&scaron;njak
  author_email: ihusnja4@gmail.com
  author_url: http://ui-stuff.com/
  date: '2012-08-17 07:32:59 +0000'
  date_gmt: '2012-08-17 07:32:59 +0000'
  content: "I very rarely use __call, mostly since I don't prefer dynamic method calls.
    As for code writing, if method name is misspelled then that is really not applications
    problem -- its programmers fault.\r\n\r\nBut using __call for detecting errors
    is quite good option since it allows you much more diagnostics to include in your
    error handling or even to trigger alternative calls.\r\n\r\nNote that __call magic
    method is triggered when inaccessible method is invoked whether method really
    doesn't exist or it's defined as private/protected:\r\n\r\nAn example:\r\n\r\nclass
    X\r\n{\r\n    public $_a;\r\n    protected $_b;\r\n    private $_c;\r\n    public
    function __construct($a, $b, $c)\r\n    {\r\n        $this->_a = $a;\r\n        $this->_b
    = $b;\r\n        $this->_c = $c;\r\n    }\r\n    public function a()\r\n    {\r\n
    \       return $this->_a;\r\n    }\r\n    protected function b()\r\n    {\r\n
    \       return $this->_b;\r\n    }\r\n    private function c()\r\n    {\r\n        return
    $this->_c;\r\n    }\r\n    public function __call($method, $args)\r\n    {\r\n
    \       if (method_exists($this, $method)) {\r\n            // use reflectio
    to figure visibility\r\n            $reflector = new \\ReflectionClass(get_class($this));\r\n
    \           $visibility = $reflector->getMethod($method)->isPrivate()? 'Private':
    'Protected';\r\n            throw new \\Exception($visibility . \" method \\\"{$method}\\\"
    is called\");\r\n        }\r\n        throw new \\Exception(\"Unexisting method
    \\\"{$method}\\\" is called\");\r\n    }\r\n}\r\n// test\r\ntry {\r\n
    \   $x = new X(\"abc\", 3, true);\r\n    echo '$x->a() = ' . $x->a() . ''; //
    ok\r\n    echo '$x->b() = ' . $x->b() . ''; // exception thrown\r\n} catch
    (\\Exception $e) {\r\n    echo $e->getMessage(). '';\r\n}\r\ntry {\r\n    echo
    '$x->c() = ' . $x->c() . ''; // exception thrown\r\n} catch (\\Exception
    $e) {\r\n    echo $e->getMessage(). '';\r\n}\r\ntry {\r\n    echo '$x->d() = '
    . $x->d() . ''; // exception thrown\r\n} catch (\\Exception $e) {\r\n
    \   echo $e->getMessage(). '';\r\n}\r\n\r\n---- RESULT ----\r\n\r\n$x->a() = abc\r\nProtected
    method \"b\" is called\r\nPrivate method \"c\" is called\r\nUnexisting method
    \"d\" is called\r\n\r\n\r\nThere is no other way than using reflection to detect
    if method is private or protected so if it is really of no difference to you,
    don't use reflection.\r\n\r\nBy using __get and __set magic methods same diagnostic
    may be used on properties in order to detect faulty calls since PHP by default
    is immune to nonexistent property calls (not even notice is risen), but for calling
    protected or private properties PHP will react with fatal error."
- id: 108
  author: BJRhodes
  author_email: bjrhodes199@hotmail.com
  author_url: ''
  date: '2012-08-17 13:16:28 +0000'
  date_gmt: '2012-08-17 13:16:28 +0000'
  content: "Can you not avoid these problems somewhat by type-hinting your injected
    dependencies with an interface, then ensuring that your injected classes correctly
    implement that interface?\r\n\r\nTrue, you'll still get a fatal error, but you'll
    get it whenever you inject that class (the typehint will fatal), or whenever that
    class is loaded (the implements declaration will fatal) which will make it much,
    much harder to miss. \r\n\r\nThis will prevent fatals in staging / production
    by being much more likely to throw them in development."
- id: 109
  author: Oscar Merida
  author_email: oscar@musketeers.me
  author_url: http://musketeers.me/
  date: '2012-08-17 15:50:19 +0000'
  date_gmt: '2012-08-17 15:50:19 +0000'
  content: On development, you should really take the time to fix anything that causes
    a PHP_NOTICE too, usually its a clue from the Zend engine that something could
    be wrong.
- id: 111
  author: mario
  author_email: no@dodgeit.com
  author_url: ''
  date: '2012-08-17 21:26:45 +0000'
  date_gmt: '2012-08-17 21:26:45 +0000'
  content: Pretty APIs are pretty. And they are the perfect use case for such scripting
    language features. But obviously overdone magic methods could also make big application
    structures harder to understand and manage.
- id: 112
  author: Juan Basso
  author_email: jrbasso@gmail.com
  author_url: http://engineering.zumba.com/
  date: '2012-08-18 00:48:19 +0000'
  date_gmt: '2012-08-18 00:48:19 +0000'
  content: "I implemented your idea of register_shutdown_function() in CakePHP framework.
    We also use the same logic in our company and it really solves the problem to
    show fancy 500 error pages and have a better log.\r\n\r\nIf you would like to
    see the code in the framework, look https://github.com/cakephp/cakephp/blob/master/lib/Cake/Core/App.php#L907-927
    and https://github.com/cakephp/cakephp/blob/master/lib/Cake/Error/ErrorHandler.php#L198-217\r\n\r\nThe
    use of __call() is a bad approach in my opinion. It is harder to maintain and
    don't cover all the cases."
- id: 129
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2012-08-25 19:28:25 +0000'
  date_gmt: '2012-08-25 19:28:25 +0000'
  content: "Yes, using interfaces would help locate all classes that we need to upgrade
    but on the other hand if by mistake we forget this step errors will start showing
    on other parts of application.\r\n\r\nStill it is a very good sugestion tnx!"
- id: 130
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2012-08-25 19:29:39 +0000'
  date_gmt: '2012-08-25 19:29:39 +0000'
  content: We do have a zero error policy (this includes anything going into our error
    handler)
- id: 132
  author: msvrtan
  author_email: miro@mirosvrtan.me
  author_url: http://www.mirosvrtan.me/
  date: '2012-08-25 20:18:36 +0000'
  date_gmt: '2012-08-25 20:18:36 +0000'
  content: 'I wrote a new post about how this should be supported natively: http://www.mirosvrtan.me/blog/2012/08/php-fatal-errors-into-exceptions-natively/'
---
<p>Two years ago we built a small class for easier logging and reporting of errors inside our applications by using <a href="http://php.net/manual/en/function.set-error-handler.php" target="_blank">set_error_handler()</a>. We built it cause:</p>
<p>1) In development mode error display can cause problems</p>
<p>We found ourselves in some situations where PHP notices would be shown inside javascript or hidden elements and it was giving us whole bunch of problems. By using our custom error handler we are able to show errors on the bottom of the page.</p>
<p>2) Staging server reporting</p>
<p>On staging servers we needed fast notifications of any errors so we implemented emailing of all errors to developers which enabled us to react much faster when something goes wrong. </p>
<p>3) Production server reporting</p>
<p>On some smaller productions we have enabled email notifications but on larger ones that was not an option so we decided to log those errors into files which we then can easily pull home. Yes Apache can do this for us too but we needed more information on each error.</p>
<p>If you have any experience with set_error_handler() function then you know that it can not catch fatal errors. There is also a solution for catching them with usage of <a href="php.net/manual/en/function.register-shutdown-function.php" target="_blank"> register_shutdown_function() </a> and I will be testing this implementation very soon (not implemented yet). </p>
<p>But what if we can transform some of those fatal errors into exceptions? We already have a lot of catch blocks prepared and although register_shutdown_function() will give us a report about error, it will show user a broken page instead of a nice 500 Server error custom page. Also maybe that fatal error would occur in some part of process that we already have covered with catch blocks and rest of the page would be shown normally. One of most often fatal errors I proudly produce is a call to undefined method in class that was injected as a dependency. </p>
<p>So my idea is to throw exception in __call magic method and those fatal errors will be transformed into something I can work with. Now my main worry is why PHP is not behaving like that already? Am I missing/forgetting something? </p>
<p>Suggestions and comments are welcomed!</p>
