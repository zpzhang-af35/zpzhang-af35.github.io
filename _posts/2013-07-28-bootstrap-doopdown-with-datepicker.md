---
layout: post
title: "bootstrap dropdown with datepicker"
description: ""
category: bootstrap
tags: [bootstrap, datepicker]
---
这个问题着实困扰我了一段时间。之前的临时解决方案，都修改bootstrap的源文件了。正好要用新版的affix特性。于是得升级。修改源文件只能解一时之急啊，所以，仔细研究了一个源文件。

最后那几行，说明调用clearmenu的条件。很明显，当一个click事件冒到document的时候，就要关闭了。因为在datepicker面板上的click事件，不属于dropmenu的序列，于是，自然要关闭这个下拉菜单了。

于是解决方案如下：在click事件到达document之前它不在往上冒。因为datepicker的div是动态添加的，绑定事件有困难，所以直接在他的父级<body>上绑定。然后分析事件来源，当是来自datepicker内部元素是，不再冒泡。因为在body接到click之前，datepicker自己已经完成他的事儿了。所以不影响什么。

代码如下：

{% include JB/setup %}