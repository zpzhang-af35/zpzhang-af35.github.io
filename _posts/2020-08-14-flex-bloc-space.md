---
layout: post
title: "flex布局下块间空间均分的方法"
description: ""
category: 
:tags: []
---
不多说了，直接上代码

HTML部分

```
<div class="booksContainer">
	<div class="bookContainer"></div>
	<div class="bookContainer"></div>
</div>
```

CSS部分

```
.booksContainer{
  display: flex;
  flex-flow: row;
  width: 100%;
  justify-content: space-evenly;
}

.bookContainer{
  background-color: white;
  flex-basis: calc(50% - 24px)
}
```

这个样式实现了，一个booksContainer中横排两个bookContainer。两个book和两边都空16px。

那个-24px怎么算呢？

因为三个空16px一共48px，所以一个元素需要在50%基础上贡献24px喽。

附上效果演示：http://jsrun.net/3NLKp/

{% include JB/setup %}