---
layout: post
title: "zend2自定义helper中使用已有的helper"
description: ""
category: zend
tags: [zend helper customer]
---
其实挺简单的，示例代码如下：

	public function __invoke($contrycode) {
        $translate = $this->getView()->plugin('translate');
        $output = $translate('France');
        return $output;
    }
    
getview返回一个phprenderer的实例，其中的plugin函数，返回的是一个plugin instance，也就是一个helper的实例，然后可以直接用了。

{% include JB/setup %}
