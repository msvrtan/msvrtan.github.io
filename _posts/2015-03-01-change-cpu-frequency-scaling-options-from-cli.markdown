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

Depending on what type of work I'm doing I use different CPU options. While there is no need to blast CPU while surfing or doing some undemanding tasks, when coding or testing I prefer to have CPU frequency high to speed things up.

Until some time ago I used to modify CPU governor or frequency using GUI but decided to switch to command line: one command instead of setting it up for each core using GUI (in my case 4 which means 8 clicks). To have it done on Ubuntu based maschines you'll need to install 'linux-tools-common':

```
  sudo apt-get install linux-tools-common
```

Instead of setting the exact frequency, I prefer to set governor. For instance 'performance' one will keep CPU on highest frequency while others (powersave, conservative and ondemand) will scale CPU frequency based on current CPU usage (more usage higher the frequency).
  
To get my maschine into performance mode:

```
  sudo cpupower frequency-set -g performance
```

To save battery or your monthly energy bill  
  
```  
  sudo cpupower frequency-set -g powersave
```


If you want to force exact frequency (example shows how to set frequency to 2Ghz)

```  
  sudo cpupower frequency-set -f 20000000
```


