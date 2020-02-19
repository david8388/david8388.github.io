---
layout: post    
title: 排序演算法(快速排序法、合併排序法)
date: 2020-02-19 20:55
categories: [SortAlgorithm, QuickSort, MergeSort]
---

## 快速排序法

快速排序法(Quick Sort)，又稱劃分交換排序(Partition exchange sorting)，操作如下

假設有N筆紀錄分別為R1，R2，R3，...

1. 選澤第一筆當作基準值(Pivot)

2. 由左至右i=2,3, ..., n，`一直找到大於等於`基準值的數

3. 由右至左j=n, n-1, n-2, ..., 2，`一直找到小於等於`基準值的數

4. 當 i < j時，則Ri與Rj互換，否則R1與Rj互換

![pic](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)

`時間複雜度為n log(n)`

## 合併排序法

合併排序法(Merge Sort)，將數列分割後，在進行整合的排序方法

如下圖：

![pic](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

資料為：[6, 5, 3, 1, 8, 7, 2, 4]

### 先進行分割 

第一輪先將資料對半，因此會分成[6, 5, 3, 1] 及 [8, 7, 2, 4]

第二輪再將資料對半，因此會分成[6, 5]、[3, 1]、[8, 7]、[2, 4]

第三輪將資料再度對半，因此會分成[6] [5] [3] [1] [8] [7] [2] [4]

## 再整合

由頭至尾，兩組資料進行合併

第一輪：[5, 6] [1, 3] 及 [7, 8] [2, 4]

第二輪：[1, 3, 5, 6] 及 [2, 4, 7, 8]

第三輪：[1, 2, 3, 4, 5, 6, 7, 6]

`時間複雜度為n log(n)`


參考資料：

- [初學者學演算法｜排序法進階：合併排序法](https://medium.com/appworks-school/%E5%88%9D%E5%AD%B8%E8%80%85%E5%AD%B8%E6%BC%94%E7%AE%97%E6%B3%95-%E6%8E%92%E5%BA%8F%E6%B3%95%E9%80%B2%E9%9A%8E-%E5%90%88%E4%BD%B5%E6%8E%92%E5%BA%8F%E6%B3%95-6252651c6f7e)

- [合併排序](https://zh.wikipedia.org/wiki/%E5%BD%92%E5%B9%B6%E6%8E%92%E5%BA%8F)

- [Comparison Sort: Quick Sort(快速排序法)](http://alrightchiu.github.io/SecondRound/comparison-sort-quick-sortkuai-su-pai-xu-fa.html)
