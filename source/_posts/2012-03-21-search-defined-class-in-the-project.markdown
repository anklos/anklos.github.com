---
layout: post
title: "Search defined class in the project"
date: 2012-03-21 17:20
comments: true
categories: technical
---

Recently I came across with a problem of searching defined class in the project.

I thought it would be easy to just use *defined?('klass'.constantize)*
.

However, *defined?(kclass)* works but *defined?('klass'.constantize)* doesn't.

It is very weired, right? Because *kclass* is supposed to be equal to *'klass'.constantize*.

I tried to use other methods like get_const. But it will raise name error for checking class inside a module like *ModuleA::ModuleB::Klass*. No idea.

A simple hack solution:
{% codeblock lang:rb %}
def present?(name)
  begin
    eval name
      true
    rescue
      false
  end
end
{% endcodeblock %}
Jesus..not good.

