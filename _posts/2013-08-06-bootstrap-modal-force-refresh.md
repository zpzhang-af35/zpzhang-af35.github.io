---
layout: post
title: "bootstrap modal force refresh"
description: ""
category: bootstrap
tags: [bootstrap, modal]
---

实验发现，光清空是不行的。于是在hidden时加上如下一行：

	$(this).data('modal').$element.removeData();
	
大功告成。至于$element，是源代码里的东西，仅仅是个属性。
{% include JB/setup %}
