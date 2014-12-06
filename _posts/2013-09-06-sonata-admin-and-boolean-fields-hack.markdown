---
layout: post
status: publish
published: true
title: Sonata Admin and boolean fields 'hack'
author:
  display_name: msvrtan
  login: orimblog
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_login: orimblog
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
wordpress_id: 443
wordpress_url: https://www.mirosvrtan.me/blog/?p=443
date: '2013-09-06 16:06:28 +0000'
date_gmt: '2013-09-06 15:06:28 +0000'
categories:
- php
tags:
- symfony2
- SonataAdmin
comments: []
permalink: /blog/2013/09/sonata-admin-and-boolean-fields-hack/
---
<p>If you are using Sonata Admin Bundle (SonataAdminBundle) and want to support persisted boolean fields you will have to define that property in your Entity as <strong>nullable</strong>.</p>
<pre lang="php">    /**<br />
     * @var boolean<br />
     *<br />
     * @ORM\Column(name="myFavoriteBooleanField", type="boolean", nullable=true)<br />
     */<br />
    private $myFavoriteBooleanField;</pre></p>
<p>Otherwise Sonata Admin will expect you to have this field checked and will not allow you to set value as 'false'. </p>
<p>Another important detail, in validation do not set this field as NotBlank since it will cause same problems with unavailability of 'false' value to choose.</p>
<p>I'm not sure if this is a but or not :(</p>
