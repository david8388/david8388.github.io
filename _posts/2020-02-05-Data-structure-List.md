---
layout: post
title: 資料結構-鏈結串列(List)
date: 2020-02-05 21:20
categories: [DataStructure, List]
---

## 資料結構
資料結構(Data Structure, DS)，代表將資料有組織的存放在記憶體中，以提升程式的執行效率

## 鏈結串列(List)

- `每一個元素可以當作是一個Node(節點)`，例如下圖的12，就可以當作一個Node

- `一個Node會儲存兩份資訊，本身的值及指向下一筆資料在記憶體的位址`，藉此將多個Node鏈結成串列(Linked List)


## 鏈結串列的種類

1. 單向鏈結串列：包含兩個值`目前節點的值`和一個`指向下一個節點的連結`，最後一個Node指標會指向Null
![pic](https://upload.wikimedia.org/wikipedia/commons/6/6d/Singly-linked-list.svg)

2. 雙向鏈結串列：每個Node有兩個指標，一個`指向上一個節點的連結`，一個`指向下一個節點的連結`以及`目前節點的值`，第一個節點之前儲存一個永遠不會被刪除或者移動的虛擬節點
![pic](https://upload.wikimedia.org/wikipedia/commons/5/5e/Doubly-linked-list.svg)

## 特性

- 不像Array有Index，找到特定資料(Node)，需從頭(HEAD)開始找起，`搜尋複雜度為O(n)`

- 新增/刪除元素，只要Node調整pointer即可，`新增/刪除複雜度為O(1)`，但是`尋找特定Node執行新增刪除，可能會需要O(n)的時間`

- 需要`額外記憶體儲存指標(pointer)`

- 非連續的方式儲存在記憶體


參考資料：

- [Linked List: Intro(簡介)](http://alrightchiu.github.io/SecondRound/linked-list-introjian-jie.html)

- [《演算法圖鑑》第一章：資料結構](https://medium.com/change-or-die/%E6%BC%94%E7%AE%97%E6%B3%95%E5%9C%96%E9%91%91-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-10d5a6337be5)

- [鏈結串列 Linked List](https://ithelp.ithome.com.tw/articles/10216257)

- [連結串列](https://zh.wikipedia.org/wiki/%E9%93%BE%E8%A1%A8)