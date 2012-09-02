---
layout: post
title: "Best way to do a find/replace in several files?"
date: 2012-06-02 00:05
comments: true
categories: technical
---

{% codeblock %}find . -type f -print0 | xargs -0 -n 1 sed -i -e 's/from/to/g'{% endcodeblock %}

Be noted that this way would break git index because it will also replace the files in the .git folder. So specify files types before you run it or you run it in the sub-directory instead of root directory.
