---
title: JavaScript 解構賦值
date: 2019-03-12 15:45
categories: [JavaScript, ECMAScript]
---

JavaScript 的解構賦值, 可以將`陣列`、`物件`中的資料取出成為一個獨立變數

### Destructuring Objects

```javascript
const personalInfo = {
  firstName: "David",
  lastName: "Wu",
  gender: "Male",
  city: "Taichung"
};
```

若要取得 personalInfo 這個物件的 firstName 及 city 屬性則可以這樣使用

```javascript
const { firstName, city } = personalInfo;
console.log(firstName); // David
console.log(city); // Taichung
```

但假如物件裡的屬性名稱值很長, 就會需要將取出來的值做 rename

```javascript
const { firstName: fn, lastName: ln } = personalInfo;
console.log(fn); // David
console.log(ln); // Wu
```

### Destructuring Arrays

依照陣列位置, 依序輸入變數值名稱便能取得陣列值

```javascript
const [favor1, favor2, favor3] = ["baseball", "basketball", "tennis"];

console.log(favor1); // baseball
console.log(favor2); // basketball
console.log(favor3); // tennis
```

若`變數值宣告次數超過陣列長度值`, 那麼`超過的變數名稱則為 undefined`

```javascript
const [favor1, favor2] = ["baseball"];

console.log(favor1); // baseball
console.log(favor2); // undefined
```

---

參考資料：

- [Destructuring_assignment](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
