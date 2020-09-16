---
layout:     post
title:      "Vue源码学习-数据双向绑定"
date:       2019-11-18 18:00:00
author:     "Hxz"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 框架
---

# 如何实现一个Vue的数据双向绑定

在vue中数据双向绑定主要是用defineProperty这个方法来实现监听数据变化，来触发相应的方法。
