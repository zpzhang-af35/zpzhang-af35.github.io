---
layout: post
title: "在zend的view中使用paginatorControler里的参数"
description: ""
category: zend
tags: [zend]
---
今天修改站里的一个issue。显示一个类似于1 to 20 of 100这样的东西，在所有的数据据表前。因为都做了分页处理，所以这几个参数自然要去zend\paginator里找了。

官方文档里有提供，在Zend\View\Helper\PaginationControl里提供了如下参数：

Property  |  Type  |  Description
--------  |  ----  |  -----------
first  |  integer  |  First page number (i.e., 1)
firstItemNumber | integer | Absolute number of the first item on this page
firstPageInRange | integer | First page in the range returned by the scrolling style
current | integer | Current page number
currentItemCount | integer | Number of items on this page
itemCountPerPage | integer | Maximum number of items available to each page
last | integer | Last page number
lastItemNumber | integer | Absolute number of the last item on this page
lastPageInRange | integer | Last page in the range returned by the scrolling style
next | integer | Next page number
pageCount | integer | Number of pages
pagesInRange | array | Array of pages returned by the scrolling style
previous | integer | Previous page number
totalItemCount | integer | Total number of items

   
例子里给了使用方法，就是直接

	echo $this->totalItemCount;

但是直接在view中用，不行。例子里的代码都是在单独一个partial里的。那我要在view中使用怎么办呢？于是关键就成了，在partial里，这个this是什么。

查看了一下zend的核心代码，原来这个this是叫pages，类型是\zend\stdlib，通过以下方法等到：

	paginator->getpages()

于是，在view中就可以这样使用这些参数啦！

	<?php echo $this->orders->getPages()->firstItemNumber;?>
	
其中那个orders是从controller里传来的paginator.

完整代码如下：

	showing <?php echo $this->orders->getPages()->firstItemNumber . ' to ' . $this->orders->getPages()->lastItemNumber . ' of ' . $this->orders->gettotalItemCount() ?>

又是美好的一天！

{% include JB/setup %}

