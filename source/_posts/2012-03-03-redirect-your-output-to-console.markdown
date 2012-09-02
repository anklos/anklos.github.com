---
layout: post
title: "Redirect your output to console"
date: 2012-03-03 23:20
comments: true
categories: technical
---
Below are some tricks I learnt from one thread in ruby-china forum.


Redirect log output to console:
{% codeblock lang:rb %}
ActiveRecord::Base.logger = Logger.new(STDOUT)
ActiveResource::Base.logger = Logger.new(STDOUT)
ActionController::Base.logger = Logger.new(STDOUT)
{% endcodeblock %}

You can also customize the color:
{% codeblock lang:rb %}
class String
  def colorize(color, options = {})
    background = options[:background] || options[:bg] || false
    style = options[:style]
    offsets = ["gray","red", "green", "yellow", "blue", "magenta", "cyan","white"]
    styles = ["normal","bold","dark","italic","underline","xx","xx","underline","xx","strikethrough"]
    start = background ? 40 : 30
    color_code = start + (offsets.index(color) || 8)
    style_code = styles.index(style) || 0
    "\e[#{style_code};#{color_code}m#{self}\e[0m"
  end
end
{% endcodeblock %}

