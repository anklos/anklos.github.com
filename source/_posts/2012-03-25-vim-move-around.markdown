---
layout: post
title: "vim: move around"
date: 2012-03-25 00:55
comments: true
categories: technical
---

e: Move to the end of a word.

w: Move forward to the beginning of a word.

b: Move backward to the beginning of a word.

$: Move to the end of the line.

0: Move to the beginning of the line.

^: Move to the first non-blank character of the line.

): Jump forward one sentence.

(: Jump backward one sentence.

}: Jump forward one paragraph.

{: Jump backward one paragraph.

H: Jump to the top of the screen.

M: Jump to the middle of the screen.

L: Jump to the bottom of the screen.

mb & 'b: mark a line and jump to that line

'': Return to the line where the cursor was before the latest jump.(Two single quotes.)

``: Return to the cursor position before the latest jump (undo the jump).(Two back ticks. This is above the Tab key on some keyboards.)

%: Jump to corresponding item, e.g. from an open brace to its matching closing brace.
