---
layout: post    
title: HTML URL編碼
date: 2020-02-23 14:50
categories: [HTML, URL, Encoding]
---

## What is URL Encoding ?

URL encoding 就是`將字元轉換成在網路上可以傳遞的格式`

## 為什麼需要Encoding ?

`URLs 只能在網路上傳遞 ASCII character-set`，當任何一個字元`不是字母、數字或是有使用保留字[註1]`就需要做Encode

註1：保留字有 

```
; , / ? : @ & = + $ - _ . ! ~ * ' ( ) #
```

## 舉例

以下表單來說

![pic](https://i.imgur.com/WhF2RdZ.png)

再Email的地方有`使用到@這個保留字`，所以傳遞的時候，會將這個保留字`進行encode`

在網頁上開啟開發者工具，看到NetWork，就可以看到編碼、解碼的區別

以下圖片為編碼

![pic](https://i.imgur.com/Zpfak4r.png)

參考資料：

- [Url Encoding References](https://guide.freecodecamp.org/html/url-encoding-reference/)

- [HTML URL Encoding Reference](https://www.w3schools.com/tags/ref_urlencode.ASP)

- [HTML ASCII Reference](https://www.w3schools.com/charsets/ref_html_ascii.asp)