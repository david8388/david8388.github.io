---
layout: post    
title: 資料結構- 堆積(Heap)
date: 2020-02-11 20:30
categories: [DataStructure, Heap]
---

## 堆積

堆積(Heap)，是一種`樹狀結構的資料結構`，如下圖，`最上方稱為根節點(Root)`，每個節點最多可以擁有兩個節點，當`根節點的值小於等於子節點`的值，此堆積稱之為`最小堆積(Min Heap)`; 反之，當`根節點的值大於等於子節點`的值，此堆積稱之為`最大堆積(Max Heap)`

![pic](https://upload.wikimedia.org/wikipedia/commons/3/38/Max-Heap.svg)


## 時間複雜度

操作  | 時間  
------|:-----
新增   | O(log n)
刪除   | O(log n)  

## 特性

- `最上方稱之為根節點(Root)`，`每個節點最多只有兩個節點`

- 堆積是一棵完全樹，除了最底層，其他層節點都會被填滿，最底層盡可能由左至右新增資料

- 資料會`從最下層開始新增資料`，若資料該層已經滿了，則往下產生新的一層並追加資料

參考資料：

- [堆積](https://zh.wikipedia.org/wiki/%E5%A0%86%E7%A9%8D)

- [《演算法圖鑑》第一章：資料結構](https://medium.com/change-or-die/%E6%BC%94%E7%AE%97%E6%B3%95%E5%9C%96%E9%91%91-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-10d5a6337be5)