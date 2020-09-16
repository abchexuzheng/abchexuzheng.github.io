---
layout:     post
title:      "算法解析—链表中倒数第k个节点"
date:       2020-09-16 18:00:00
author:     "Hxz"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 框架
---

# 算法解析—链表中倒数第k个节点

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。

# 思路

双指针：先让两个指针距离相差k - 1，然后同时前进，知道后一个指针到达末尾

# 代码

``` js
var getKthFromEnd = function(head, k) {
  // 指针
  let p = head
  // 让2个指针差为k - 1
  while(k > 1) {
    if (p.next) {
      p = p.next
      k--
    } else {
      return null
    }
  }
  // 指针前进
  while(p.next) {
    p = p.next
    head = head.next
  }
  return head
};
```
