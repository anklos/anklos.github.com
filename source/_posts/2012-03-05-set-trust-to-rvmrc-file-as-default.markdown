---
layout: post
title: "Set trust to .rvmrc file as default"
date: 2012-03-05 23:02
comments: true
categories: technical
---
If you use .rvmrc in your project to control the ruby version, you have probably seen the below message when you enter the project directory:

{% codeblock %}
Do you wish to trust this .rvmrc file? (/home/www/apps/current/.rvmrc)
y[es], n[o], v[iew], c[ancel]> n
{% endcodeblock %}
In order to pass this, you could just put one line in /etc/.rvmrc or ~/.rvmrc:
{% codeblock %}
rvm_trust_rvmrcs_flag=1
{% endcodeblock %}
