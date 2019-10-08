---
layout:     post
title:      "算法学习笔记--回溯算法--N皇后"
date:       2019-10-08 18:00:00
author:     "Hxz"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 算法
---

# 算法学习笔记--回溯算法--N皇后

## 什么是回溯算法

先来了解一下什么时回溯算法。回溯的处理思想，有点类似枚举搜索。我们枚举所有的解，找到满足期望的解。为了有规律地枚举所有可能的解，避免遗漏和重复，我们把问题求解的过程分为多个阶段。每个阶段，我们都会面对一个岔路口，我们先随意选一条路走，当发现这条路走不通的时候（不符合期望的解），就回退到上一个岔路口，另选一种走法继续走。

## 接下来来看下题目，N皇后问题

n 皇后问题研究的是如何将 n 个皇后放置在 n×n 的棋盘上，并且使皇后彼此之间不能相互攻击。

![Image text](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/8-queens.png)

上图为 8 皇后问题的一种解法。

给定一个整数 n，返回所有不同的 n 皇后问题的解决方案。

每一种解法包含一个明确的 n 皇后问题的棋子放置方案，该方案中 'Q' 和 '.' 分别代表了皇后和空位。

## 求解思路

N皇后问题非常适合使用回溯算法来做，我们把每一行选择值分为一个阶段，在放置值的过程中，我们不停检查当前的方法，是否满足要求，满足就继续跳到下一行放置棋子，不满足就换一种方法，继续尝试。

## 代码

首先是写出递推公式

``` js
function getRowPos (rowIndex, arr = []) {
    // n个棋子都放置完成，返回结果
    if (rowIndex === n) {
        result.push(arr)
        return
    }
    for (let col = 0; col < n; col ++) {
        // 如果是第一行，就直接放入，然后跳到下一行
        if (rowIndex === 0) {
            arr = [col]
            getRowPos(rowIndex + 1, arr)
        } else {
            // 判断是否符合要求，符合就插入并继续跳到下一行
            if (isOk(rowIndex, col, arr)) {
                const newArr = [...arr]
                newArr.push(col)
                getRowPos(rowIndex + 1, newArr)
            }
        }
    }
}
```

然后写出判断条件

``` js
function isOk (row, col, arr) {
    let leftTop = col - 1
    let rightTop = col + 1
    for (let i = row - 1; i >= 0; i --) {
        const lastPos = arr[i]
        // 判断正上方是否有棋子
        if (lastPos === col) {
            return false
        }
        // 判断左上方是否有棋子
        if (leftTop >= 0 && lastPos === leftTop) {
            return false
        }
        // 判断右上方是否有棋子
        if (rightTop < n && lastPos === rightTop) {
            return false
        }
        leftTop--
        rightTop++
    }
    return true
}
```

最后格式化输出

``` js
// 格式化输出
function print () {
    return result.map(item => {
        return item.map(item2 => {
            let str = ''
            for (let i = 0; i < n; i++) {
                if (item2 === i) {
                    str += 'Q'
                } else {
                    str += '.'
                }
            }
            return str
        })
    })
}
```

完整的代码

``` js

var solveNQueens = function(n) {
    const result = []   
    function getRowPos (rowIndex, arr = []) {
        // n个棋子都放置完成，返回结果
        if (rowIndex === n) {
            result.push(arr)
            return
        }
        for (let col = 0; col < n; col ++) {
            // 如果是第一行，就直接放入，然后跳到下一行
            if (rowIndex === 0) {
                arr = [col]
                getRowPos(rowIndex + 1, arr)
            } else {
                // 判断是否符合要求，符合就插入并继续跳到下一行
                if (isOk(rowIndex, col, arr)) {
                    const newArr = [...arr]
                    newArr.push(col)
                    getRowPos(rowIndex + 1, newArr)
                }
            }         
        }
    }

    // 判断该位置是否合理
    function isOk (row, col, arr) {
        let leftTop = col - 1
        let rightTop = col + 1
        for (let i = row - 1; i >= 0; i --) {
            const lastPos = arr[i]
            // 判断正上方是否有棋子
            if (lastPos === col) {
                return false
            }
            // 判断左上方是否有棋子
            if (leftTop >= 0 && lastPos === leftTop) {
                return false
            }
            // 判断右上方是否有棋子
            if (rightTop < n && lastPos === rightTop) {
                return false
            }
            leftTop--
            rightTop++
        }
        return true
    }

    // 格式化输出
    function print () {
        return result.map(item => {
            return item.map(item2 => {
                let str = ''
                for (let i = 0; i < n; i++) {
                    if (item2 === i) {
                        str += 'Q'
                    } else {
                        str += '.'
                    }
                }
                return str
            })
        })
    }
    getRowPos(0)
    return print()
};
```
