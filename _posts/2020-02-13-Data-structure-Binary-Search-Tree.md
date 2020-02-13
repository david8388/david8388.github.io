---
layout: post    
title: 資料結構- 二元搜尋樹(Binary Search Tree)
date: 2020-02-13 20:30
categories: [DataStructure, BinarySearchTree]
---

## 二元搜尋樹

二元搜尋樹(Binary Search Tree)，是一種`樹狀資料結構`，並具有以下特性

1. 任意節點的左子樹不為空，則左子樹上所有節點的值均小於它的根節點的值

2. 任意節點的右子樹不為空，則右子樹上所有節點的值均大於它的根節點的值

![pic](http://www.csie.ntnu.edu.tw/~u91029/BinaryTree1.png)

## 二元搜尋樹的類型

![pic](http://www.csie.ntnu.edu.tw/~u91029/BinaryTree2.png)

1. full binary tree：除了樹葉外，其餘節點都有左、右子節點

2. complete binary tree：各層節點全滿，除了最後一層，最後一層節點全部靠左

3. perfect binary tree：各層節點全滿，同時也是full binary tree及complete binary tree    

## 時間複雜度

操作  | 時間  
------|:-----
搜尋   | O(log n) 
新增   | O(log n)
刪除   | O(log n)  

搜尋資料的時候，從根節點開始查詢，比根節點小從左子樹找起，比根節點大從右子樹找起，所以時間複雜度是O(log n)

新增資料亦是，從根節點開始比大小，比根節點小從左子樹開始，比根節點大從右子樹開始，直到找到位置最插入，所以時間複雜度是O(log n)

刪除的情況就比較多元，以下參考 [shenyun2304](https://github.com/shenyun2304/swift-algorithm-club-zhTW/tree/master/Binary%20Search%20Tree#%E5%88%AA%E9%99%A4%E7%AF%80%E9%BB%9E)所寫的文章

1. 若是`刪除葉節點`，`直接移除即可`，不用做取代

2. 當`刪除的節點只有一個子節點`，則用該`子節點取代刪除節點的位置`

3. `移除其餘節點時`，則選擇`該節點中左子樹的最大值`，`或是右子樹的最小值來取代`

參考資料：

- [Binary Tree](http://www.csie.ntnu.edu.tw/~u91029/BinaryTree.html)

- [二元搜尋樹](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%85%83%E6%90%9C%E5%B0%8B%E6%A8%B9)

- [[資料結構] 二元搜尋樹 (Binary Search Tree)](https://ithelp.ithome.com.tw/articles/10205875)

- [[資料結構] 樹 Tree](https://w3c.hexschool.com/blog/bc00a810)

- [Binary Search Tree (BST) 二元搜尋樹](https://github.com/shenyun2304/swift-algorithm-club-zhTW/tree/master/Binary%20Search%20Tree#%E5%88%AA%E9%99%A4%E7%AF%80%E9%BB%9E)