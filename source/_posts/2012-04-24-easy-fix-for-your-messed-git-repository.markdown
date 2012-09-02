---
layout: post
title: "Overwrite messed local branch with remote branch"
date: 2012-04-24 23:18
comments: true
categories: technical
---
We often meet this situation on using git: we pull down the code from remote branch to a long time not updated repository and find lots of conflicts after merge. The first thought comes up to your mind is probably just overwrite the local branch by the remote one. It is not that straight forward to do this like SVN. Here I would like to introuce a full solution for this issue.

First, if you already pull down the remote branch and have a lot of conflicts in the repository, you could run the command: {% codeblock %}git reset --hard HEAD{% endcodeblock %} to drop off the changes done by last pull.

Second, rename your local branch. For example, if you want to replace your master branch, you could do {% codeblock %}git branch -m master old_master{% endcodeblock %}
    
Thirdly, get the remote master to your local master by running command: {% codeblock %}git checkout -b master origin/master{% endcodeblock %}

Now you have the latest code in your master branch. If you want to delete your old master, you can just do: {% codeblock %}git branch -D old_master{% endcodeblock %}

That's it, yeah!
