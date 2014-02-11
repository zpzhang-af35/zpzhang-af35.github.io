---
layout: post
title: "谁说java的foreach不能修改值？"
description: ""
category: 
tags: [java, foreach]
---
今天遇到个需要范围的修改值的问题，就想用foreach试试，省事呗。开始前随手一搜，发现一票人都说这个是不可能的！！但是我一试，可以啊！！代码如下：

	List<Integer> list = new ArrayList<>();
	list.add(1);
	list.add(2);
	
	List<Integer> list2 = new ArrayList<>();
	list2.add(1);
	list2.add(2);
		
	List<List<Integer>> llist = new ArrayList<>();
	llist.add(list);
	llist.add(list2);
	
	for(List<Integer> li : llist){
		li.set(0, 3);
	}
	
按照值不变理论，llist的内容是不是不变呢？错！变了！

	System.out.println(llist.get(0).get(0) +" "+ llist.get(1).get(0));
	
得到的结果是

	3 3
	
原理很简单，因为foreach每一个元素，是数组里元素的引用，因此，此引用的set函数发挥了作用。

同理，用一个List的类也是同样的结果，因为是引用的关系，＝操作当然不行了，也就是简单类型，还真没有办法……

{% include JB/setup %}
