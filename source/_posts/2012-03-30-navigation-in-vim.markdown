---
layout: post
title: "use ctags navigation in mac vim"
date: 2012-04-12 18:25
comments: true
categories: technical
---

Step1: Type command {% codeblock %}brew install ctags{% endcodeblock %}
Don't install ctags from http://ctags.sourceforge.net/. Reason is this version doesn't support ruby. I dont know why is that.. Anway, brew rocks.

Step2: GO to your vimrc file, put one line: {% codeblock %}set tags=tags;{% endcodeblock %}

Step3: GO to your project directory and run command {% codeblock %}ctags -R{% endcodeblock %}

Done! Now you can go to functin calls and simply type 'ctrl ]'. Then it will magically jump to the definition.

