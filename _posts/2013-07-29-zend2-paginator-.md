---
layout: post
title: "zend2 paginator, 返回所有的小技巧"
description: ""
category: zend
tags: [zend, paginator]
---

一句话，只要给setItemCountPerPage()传一个小于0的参数，或者一个字符非数字的参数。就是不能被转成int的参数就可以了。我就直接传了个‘all’，完事了。

{% include JB/setup %}
