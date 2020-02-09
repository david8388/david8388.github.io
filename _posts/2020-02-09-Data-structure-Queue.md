---
layout: post    
title: 資料結構- 佇列(Queue)
date: 2020-02-09 21:05
categories: [DataStructure, Queue]
---

## 佇列

佇列(Queue)，具有先進先出(First In First Out)的特性，以生活上來舉例：在排隊的時候，服務人員一定是按照順序一位一位客人進行服務，服務完當下這位，才會對下一位客人進行服務。

與堆疊處理資料的方式有點不太一樣，堆疊(Stack)的新增、彈出皆是在頂端(Top)做處理，但是`佇列`對於資料新增是在`後端(Rear)進行插入`操作，在`前端進行刪除`

![pic](https://i1.wp.com/www.fgchen.com/wp/wp-content/uploads/2016/12/120116_0009_Queue1.png?resize=460%2C221)

## 特性

- 具有`先進先出(First In First Out)`的性質

- 直接於`佇列後端(Rear)進行新增操作`，故`新增時間複雜度為O(1)`

- 直接於`佇列前端(Front)進行移除操作`，故`刪除時間複雜度為O(1)`

- 搜尋時，需要從頭遍歷整個項目來搜索，故`搜尋時間複雜度為O(n)`，


參考資料：

- [佇列](https://zh.wikipedia.org/wiki/%E9%98%9F%E5%88%97)

- [資料結構的佇列(Queues)](http://wayne.cif.takming.edu.tw/datastru/queue.pdf)

- [佇列(Queue)](http://epaper.gotop.com.tw/pdf/AEE032400.pdf)