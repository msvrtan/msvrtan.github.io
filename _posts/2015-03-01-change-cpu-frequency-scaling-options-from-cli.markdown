---
layout: post
status: publish
published: true
title: Change CPU frequency scaling options from CLI
author:
  display_name: msvrtan
  email: miro@mirosvrtan.me
  url: https://www.mirosvrtan.me/
author_email: miro@mirosvrtan.me
author_url: https://www.mirosvrtan.me/
categories:
- personal
tags: 
- linux
comments: []
permalink: /blog/2015/03/change-cpu-frequency-scaling-options-from-cli/
---

Until some time ago I used to modify CPU governor or frequency using GUI but decided to speed it up using command line. To have it done on Ubuntu based maschines you'll need to install 'linux-tools-common':

  sudo apt-get install linux-tools-common
  
To get my maschine into performance mode:

  sudo cpupower frequency-set -g performance

To save battery or your monthly energy bill  
  
  sudo cpupower frequency-set -g powersave
