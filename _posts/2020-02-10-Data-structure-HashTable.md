---
layout: post    
title: 資料結構- 雜湊表(HashTable)
date: 2020-02-10 20:15
categories: [DataStructure, HashTable]
---

## 雜湊表

雜湊表(HashTable)，根據`鍵值(key)直接查詢`在記憶體儲存的位置。也就是透過雜湊函數(hash function)，計算鍵(Key)所對應的位置，進而找到對應值(value)

![pic](https://upload.wikimedia.org/wikipedia/commons/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg)

## 碰撞

當兩筆以上不同的資料進行雜湊函數運算時有著相同的結果，此時就會發生碰撞(Collision)，碰撞問題太多，就會導致雜湊表效能變差，所以雜湊函數會盡量避免碰撞。

解決碰撞的方法有

1. 開放定址(Opening Address)：當發生碰撞時，會找出第二個替代位址儲存，若還是發生碰撞，會一直找到空的位址並且儲存值(value)

![pic](https://upload.wikimedia.org/wikipedia/commons/b/bf/Hash_table_5_0_1_1_1_1_0_SP.svg)

2. 分離鏈結法(Separate Chaining)：在每一個Hash value裡頭置放鏈結串列(Linked List)，當資料有碰撞的情況時，就將值放入鏈結串列(Linked List)之中，但需要額外儲存鏈結串列(Linked List)

![pic](https://upload.wikimedia.org/wikipedia/commons/d/d0/Hash_table_5_0_1_1_1_1_1_LL.svg)

## 特性

- 雜湊表(HashTable)利用雜湊函數hash function進行搜尋，`搜尋時間複雜度為O(1)`

- `新增、移除時間複雜度為O(1)`

- 當發生碰撞時，通常會使用`開放定址(Opening Address)`、`額外鏈結法(Separate Chaining)`這兩種方法解決

參考資料：

- [雜湊表](https://zh.wikipedia.org/wiki/%E5%93%88%E5%B8%8C%E8%A1%A8)

- [用 JavaScript 學習資料結構和演算法：字典（Dictionary）和雜湊表（Hash Table）篇](https://blog.kdchang.cc/2016/09/23/javascript-data-structure-algorithm-dictionary-hash-table/)

- [[演算法] 雜湊表(Hash Table)](https://carlos-studio.com/2018/01/21/%E6%BC%94%E7%AE%97%E6%B3%95-%E9%9B%9C%E6%B9%8A%E8%A1%A8hash-table/)

- [《演算法圖鑑》第一章：資料結構](https://medium.com/change-or-die/%E6%BC%94%E7%AE%97%E6%B3%95%E5%9C%96%E9%91%91-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-10d5a6337be5)
