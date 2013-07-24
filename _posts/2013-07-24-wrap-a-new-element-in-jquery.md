---
layout: post
title: "wrap a new element in jQuery"
description: ""
category: jquery
tags: [jquery, wrap, append]
---

## 情景

动态添加一个dropdown menu，结构如下：

	<ul>
		<li>
			<a>
			</a>
		</li>
	<ul>

其中a需要添加属性什么的。于是我想先创建a，然后加属性，然后wrap一下，然后添加到ul里。

于是下面的代码：

	$('<a>').attr('href','…').wrap('<li>').appendTo($('ul'));
	
但是，没有成功。
一查，是因为xx.wrap()后，返回的不是wrap后的对象，依然是XX本身。

于是正确代码如下：

	$('<a>').attr('href','…').wrap('<li>').parent().appendTo($('ul'));
	
增加一层parent()就好了。

当然另一种方案就是从ul开始，加一个li，再去加上a，略麻烦一些，也不是太合逻辑。代码如下：

	$('ul').append($('<li>').append($('<a>').attr('href','…'));
	
下班回家！

{% include JB/setup %}
