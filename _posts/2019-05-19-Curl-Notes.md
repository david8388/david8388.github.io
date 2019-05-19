---
layout: post
title: Curl 介紹及指令
date: 2019-05-19 14:45
categories: [Curl]
---

Curl 是一款免費且開源的軟體，目的是`利用 URL 語法傳遞資料`的命令列工具及 library，`C`可以當作 crawl，就是 url 上的資料給抓下來。

## 測試 API

API 開發完後，通常會使用 Postman 這個 GUI 工具 來測試 API 所回傳的資料，除了 Postman 之外，Curl 這個命令列工具也可以達到測試的效果

## 概要

回傳的內容可能為 JSON 或 HTML ...等，依照所輸入的 URL 而定

基本語法如下

> curl [options / URLs]

取得 NBA 的官方網站的網頁內容，所以回傳的內容為 HTML

> curl https://nba.udn.com/nba/index?gr=www

## 下載

也可以下載線上圖片到本機端， 參數可以是 -o 或是 -O

- -o：可以自訂下載的圖片名稱
- -O：直接下載

```
$ curl -o lebron.jpg https://upload.wikimedia.org/wikipedia/commons/e/ee/Lebron_wizards_2017.jpg
$ curl -O https://upload.wikimedia.org/wikipedia/commons/e/ee/Lebron_wizards_2017.jpg
```

## trace process

若要追蹤 curl 的整個過程，可以加上`--trace-ascii 指令`

下述的 process.txt ，是將追蹤的過程存入該檔案內容中

```
$ curl --trace-ascii process.txt https://www.google.com.tw/
```

## HTTP Request

kdchang 大大有整理出執行 Http request 常用指令及相關參數

| option                           | 描述                             |
| -------------------------------- | -------------------------------- |
| -X / [GET POST PUT DELETE PATCH] | 使用指定的 method 來發出 request |
| -H/                              | 設定 request 裡的 header         |
| -d/                              | 攜帶 HTTP POST Data              |

## Get

透過 IMDB 的 API 取得查詢電影資訊的資料

```
$ curl -X GET "http://www.omdbapi.com/?s=Fast&type=&apikey=yourapikey"
```

```json
{
  "Search": [
    {
      "Title": "Fast & Furious 6",
      "Year": "2013",
      "imdbID": "tt1905041",
      "Type": "movie",
      "Poster": "https://m.media-amazon.com/images/M/MV5BMTM3NTg2NDQzOF5BMl5BanBnXkFtZTcwNjc2NzQzOQ@@._V1_SX300.jpg"
    }, ...
  ],
  "totalResults": "583",
  "Response": "True"
}
```

## Post

POST JSON 資料

```
$ curl -X POST -H "Content-Type: application/json" -d '{"key1":"value1", "key2":"value2"}' "http://localhost:8080/api/resources"
```

## Put

PUT JSON 資料

```
$ curl -X PUT -H "Content-Type: application/json" -d '{"key1":"value1"}' "http://localhost:8080/api/resources"
```

## Delete

```
$ curl -X DELETE "http://localhost:8080/api/resources"
```

DELETE 資源

參考資料：

- [curl](https://curl.haxx.se/)
- [cURL 維基百科](https://zh.wikipedia.org/wiki/CURL)
- [Linux Curl Command 指令與基本操作入門教學](https://blog.techbridge.cc/2019/02/01/linux-curl-command-tutorial/)
- [Curl Common Option](https://gist.github.com/subfuzion/08c5d85437d5d4f00e58)
