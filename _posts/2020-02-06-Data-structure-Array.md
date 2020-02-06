---
layout: post
title: 資料結構-陣列(Array)
date: 2020-02-06 20:24
categories: [DataStructure, Array]
---

## 陣列

陣列(Array)，由相同類型的元素的集合所組成的資料結構，分配一塊`連續記憶體來儲存`，`利用元素的索引(index)取得對應的位址`

## 為什麼會需要陣列？

假設班上有40位學生，要如何儲存40位同學的成績呢？

為每一位同學宣告一個變數來儲存分數，這個方法是滿直覺的

```java
public class MyClass {
    public static void main(String args[]) {
      int student1 = (int)(Math.random()*100);
      int student2 = (int)(Math.random()*100);
      int student3 = (int)(Math.random()*100);
      ...
      System.out.println(student1); 87
      System.out.println(student2); 10
      System.out.println(student3); 35
      ...
    }
}
```

但人數變多，可能宣告變數就會花費了一段時間，這時候有沒有更便利的方式來解決呢？

`陣列這時候就派上用場`，此時先宣告陣列的長度


```java
public class MyClass {
    public static void main(String args[]) {
      int students [] = new int[40];
      for(int i = 0; i < 40; i++) {
            int score = (int)(Math.random()*100);
            System.out.println(score);
        }
    }
}
```

## 特性

- 分配一塊`連續記憶體來儲存`

- 取得特定位置的值只需透過Index取得資料即可，`搜尋時間複雜度為O(1)`，假如不確定資料位置，時間複雜度就會變成O(n)

- 當新增陣列值的時候，在指定值之後的所有資料都需要往後調整，例如陣列第一筆資料新增資料時，時間複雜度就會變O(n)，刪除也跟新增一樣，因此`新增/刪除的時間複雜度為O(n)`

參考資料：

- [陣列](https://zh.wikipedia.org/wiki/%E6%95%B0%E7%BB%84)

- [陣列 Array](https://ithelp.ithome.com.tw/articles/10213787)

- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)
