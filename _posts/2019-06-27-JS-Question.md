---
layout: post
title: Javascript 趣味題目
date: 2019-06-26 21:06
categories: [javascript]
---

最近在網路上看到了滿有趣的 Javascript 趣味題目，而且我也答錯，覺得自己打底必須要更精實才對！！

題目如下

![Question](https://scontent.frmq2-1.fna.fbcdn.net/v/t1.0-9/64645903_1624302044370403_6625234289577426944_o.png?_nc_cat=105&_nc_oc=AQmBliEmdQcaOg2YtFhtGcdCADN0zc12ewa7_JhSmdeCW_5aqywZUnKBMcPmNUhdI40&_nc_ht=scontent.frmq2-1.fna&oh=4c48408bb99a1868f8693e19b91ee1bc&oe=5D7ADB12)

首先要先瞭解 map 的 parameter

1. callback：產生新陣列元素的 callback function

   1-1. currentValue：迭代目前處理的元素

   1-2. index：迭代目前處理的元素索引值

   1-3. array：呼叫 map 方法的陣列

2. thisArg：執行 callback 的 this

再來瞭解 parseInt 的 parameter

1. string：待轉成數值的字串

2. radix：從 2 到 36 代表進位系統的值，預設為 10

radix 為 undefined、空、0 的話，Javascript 會

1. string 由 `"0x" or "0X"為開頭`，radix 為 `16(進制)`

2. string 由 `0` 開始，則 radix 會為 `8 or 16(進制)`，取決於各自實作

3. string 由 `其他字串開頭`，則以 `10(進制)`

註：若字串無法轉為 number，則給 NaN

瞭解完參數定義之後，再來看題目

```js
const arr = ['1', '2', '3'].map(parseInt)
console.log(arr)
```

parseInt 會接收兩個參數，此時會對應到 map callback function 的前兩個參數，也就是 currentValue 及 Index

將 parseInt 覆寫會比較明顯，給大家看接收的值為何

```js
function parseInt(el, index) {
  console.log(`${el}-${index}`)
  // "1-0"
  // "2-1"
  // "3-2"
}

const arr = ['1', '2', '3'].map(parseInt)
```

parseInt 所接收到的進位制值分別為：0 1 2

## 過程

第一個迭代元素'1'，`當 base 為 0 時，要判斷 currentValue 適用於哪種條件`，因為值皆非"0x" or "0X" or "0" 為開頭，所以預設給 10(進制)，所以第一個元素是 1

第二個迭代元素'2'，base 為 1，但是`1 進制底下沒有數字2`，無法轉換成數字，所以是 NaN

第三個迭代元素'3'，base 為 2，但是`2 進制底下只有 0 和 1`，無法轉換成數字，所以是 NaN

答案是[1,NaN,NaN]

## 延伸題

那將上述題目陣列改為['', '1', '2', '3']，結果就會不同了

```js
const arr = ['', '1', '2', '3'].map(parseInt)

console.log(arr)
```

第一個迭代元素空值，無法轉換成 10 進制，所以是 NaN

第二、三、四個迭代元素字串及基底值分別為

- 1 1

- 2 2

- 3 3

進制的最大值是 base - 1，所以這裡的迭代字串皆無法轉換，所以為 NaN

所以答案是[NaN, NaN, NaN, NaN]

參考資料：

- [Array.prototype.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
