---
layout: post
title: "给Doctrine的many to many关系加上属性"
description: "这是弄啥的？"
category: doctrine
tags: [doctrine, many-to-many, attribute]
---
此文讨论给doctrine的多对多关系属性的问题。

## 一，废话
这两天处理工作里的一个问题。订单，和订单里的商品之间的一个关系。要是直接设计数据库，反而简单些。但是我们用的是doctrine处理的，于是，麻烦了一些。

## 二、需求
1. 通过订单查到其把包含的商品，及此商品的数量
2. 通过商品查到其销售情况，也就是包含此商品的订单情况。

## 三、分析
首先说，一个订单会包含多个商品，一个商品会属于多个订单。所以商品和订单之间是多对多关系。根据BNF范式理论，这里需要三张表：

order表：
	
	idorder,…

product表：

	idproduct,…

productquantity表：

	idorder,idproduct,quantity
	
其中表3里两个id合起来做主键。
完美解决之前提出的需求。

但是。。。

如果仅仅在doctrine中声明order和product之间的manytomany关系，会自动生成表3，但是无法添加表3中的quantity属性，也就是本文题目所说的关系上的属性。

##四、解决
好吧，既然有了成功的建表方案了，我们能不能返回去推doctrine里的entity组成呢？当然了。上面三张表，对应成3个entity。其中一个order，会对应多个productquantity，而一个productquantity对应一个order。同理，一个product，对应多个productquantity，而一个productquantity，对应一个product。两边的关系都是多对一。同时，order和product之间不再有直接的联系。

于是我们有了下面的entitis：

Order

	class order{
	$idorder
	
	@onetomany,target='productquantity'	@joincolum = 'idorder'
	$productquantitys
	
	//other attribute
	//set,get
	}
	
Product

	class product{
	$idproduct
	
	@onetomany,target='productquantity'	@joincolum = 'idproduct'
	$productquantitys
	
	//other attribute
	//set,get
	}

productquantity

	class productquantity{
	$idproductquantity
	
	@manytoone,target='order'
	@joincolum = 'idorder'
	$order
	
	@manytoone,target='product'
	@joincolum = 'idproduct'
	$product
	
	//other attribute
	//set,get
	}

于是，对于需求一，我们可以

	productquantitys = order->getproductquantity;
	foreach(productquantitys as productquantity){
		productquantity->getproduct;
		productquantity->getquantity;
	}
	
同理，对于需求二：

	productquantitys = product->getproductquantity;
	foreach(productquantitys as productquantity){
		productquantity->getorder;
	}
	
OK，完事睡觉…明儿给他实现了。
{% include JB/setup %}

