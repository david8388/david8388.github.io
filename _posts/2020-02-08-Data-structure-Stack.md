---
layout: post
title: 資料結構- 堆疊(Stack)
date: 2020-02-08 10:40
categories: [DataStructure, Stack]
---

## 堆疊

堆疊(Stack)，一種後進先出(Last In First Out)的資料結構，`新增、彈出必須要在堆疊頂端執行`，舉例來說：當兵的時候，原本正在寢室休息，後來被班長叫去出公差，必須要完成出公差這件事情，才可以再回到寢室休息

## 操作

對於堆疊的操作主要有兩種

1. 新增(Push)：將資料置放於堆疊的頂端，堆疊頂堆資料變成新置入的資料

2. 彈出(Pop)：將堆疊頂端的資料移除，堆疊頂端變成移除後的最後一筆資料

![pic](https://upload.wikimedia.org/wikipedia/commons/2/29/Data_stack.svg)

Note：`新增、刪除皆是在堆疊的頂端進行操作`

## 特性

- 具有`後進先出(Last In First Out, LIFO)，先進後出(First In Last Out, FILO)`的性質

- 新增(Push)、彈出(Pop)，都是從堆疊頂端進行操作，故`新增、移除時間複雜度為O(1)`

- `搜尋時要先將資料做彈出(Pop)`，`再將彈出的資料跟搜尋的資料做比對`，直到比對成功，故`搜尋時間複雜度為O(n)`

參考資料：

- [堆疊](https://zh.wikipedia.org/wiki/%E5%A0%86%E6%A0%88)

- [《演算法圖鑑》第一章：資料結構](https://medium.com/change-or-die/%E6%BC%94%E7%AE%97%E6%B3%95%E5%9C%96%E9%91%91-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-10d5a6337be5)

- [Data](http://www.csie.ntnu.edu.tw/~u91029/Data.html)