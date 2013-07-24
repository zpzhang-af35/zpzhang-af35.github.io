---
layout: post
title: "jquery读取CSS属性的百分值"
description: ""
category: jquery
tags: [jquery, css]
---
今天在做东西的时候，遇到一个要修改progressbar长度的这么一个东西，但是bootstrap里的bar，属性是用百分值表示的，略悲剧啊。

因为jquery提供的方法里，无论是css，还是width，得到的真是真实的px值，不会返回百分值。
{% include JB/setup %}
