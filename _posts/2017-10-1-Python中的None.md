---
layout:     post
title:      Python中的None
subtitle:   有关None的一些知识
date:       2017-10-1
author:     KBOCBRE
header-img: img/post-bg-coffee.jpeg
tags:
    - Python
    - None
---



None是一个不可变对象，类型为`NoneType`,其bool值为false。
好比0是一个对象，其类型为`int`型，其bool值是false。

### Python中bool值为false的有以下几种：
进行逻辑判断时，Python中等于False的值并不只有False一个，有一套规则。对于基本类型来说，基本上每个类型都存在一个值会被判定位False，大致如下：
* 布尔型：False为False，其他为True
* 整数和浮点数：0为False，其他为True
* 字符串和类字符串类型（包括byte和Unicode），空字符串为False，其他为True
* None永远表示False

**None**可以赋值给任何变量，但是你不能创建其他NoneType对象



`总结:None是不可变对象，bool值为：False，NoneType类型，可以将其赋值给其他变量`