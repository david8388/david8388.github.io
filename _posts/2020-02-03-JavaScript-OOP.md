---
layout: post
title: JavaScript物件導向概念
date: 2020-02-03 21:10
categories: [JavaScript, OOP]
---

## 物件導向程式設計
物件導向程式設計(Object-oriented programmings，OOP)，是一種程式開發的方法，以物件的概念代表現實世界的方式。

OOP將軟體想像成一群物件交互合作所組成，而非以函數(Function)或簡單的指令交互合作所組成，簡單來說就是將`相關的屬性及函數封裝再同一個物件裡`，提高可用性及容易擴充。

## 定義類別、屬性、建構子
類別：建立某個物件的設計圖

屬性：物件的資料

建構子(constructor)：用來建立及初始化類別的物件，一個類別只能有一個constructor

## 使用ES6語法建立類別物件
看範例之前先介紹OOP的三大特性：`封裝(Encapsulation)、繼承(Inheritance)、多型(Polymorphism)`

### 封裝：`將相關屬性及函數封裝再同一個class`

請參考以下程式碼

```javascript
class Animal {
    constructor(name, age) {
        this.name = name;
        this.age = age
    }

    sayHi() {
        console.log(this.name, ' say hi')
    }

    move() {

    }
}
```

### 繼承：`定義一個類別(子類別)，並且繼承另外一個(父類別)，子類別可以取得父類別的屬性及方法`

建立一個Dog的類別並且繼承Animal類

```javascript
class Dog extends Animal {
    constructor(name, age) {
        super(name, age) 
    }

    move() {
        console.log('Walk')
    }
}

const a = new Dog('White', 2)
a.sayHi() // White  say hi
a.move()  //  Walk
```

雖然在Dog這個類別沒有定義sayHi這個方法，但因為`繼承來自Animal(父類別)的sayHi`，所以會印出在Animal類別所執行程式

而move則是`繼承並在Dog(子類別)覆寫`，所以這裡會執行子類別所執行的程式

### 多型：`不同的類別可以定義相同的方法，這些方法的有效範圍在所屬的類別中`

定義一個Cat的類別並覆寫move這個方法

```javascript
class Cat extends Animal {
    constructor(name, age) {
        super(name, age)
    }

    move() {
        console.log('Jump')
    }
}
```

現在同時利用Dog及Cat類別建立兩個實例(Instance)，並且執行move這個方法

```javascript
const pets = [new Dog('White', 2), new Cat('Yellow', 2)]
pets.forEach(pet => {
    pet.move()
})
```

雖然是同一個方法，但`執行的方法會是該類別所定義的方法`，所以Cat這個class所建立的實例在執行move的時候就會是Jump，Dog也是一樣的意思


印出來的答案如下

```javascript
Walk
Jump
```

參考資料：

- [JavaScript 物件導向介紹](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)

- [你懂 JavaScript 嗎？#18 （簡易版）物件導向概念](https://cythilya.github.io/2018/10/25/mixing-up-class-objects/)

- [Classes](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Classes)