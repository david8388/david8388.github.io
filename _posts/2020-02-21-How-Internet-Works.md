---
layout: post    
title: How Internet works?
date: 2020-02-21 20:55
categories: [ComputerScience, Internet]
---

## 瀏覽網頁

打開Google Chrome，輸入 [www.google.com](https://www.google.com/)，此時瀏覽器會回應Google的首頁，那中間的過程是如何流動的呢？

## 中間發生了什麼事？

1. 首先，`輸入 www.google.com`，會被`送到ISP`(Internet Service Provider，網際網路服務提供者)，在台灣，就是中華電信

2. `接著ISP會去查DNS`(Domain Name System，網域名稱系統)，DNS就像是一個電話簿一樣，`記載著Domain Name對應的IP Address`，以Google為例，會回傳172.217.160.78

3. ISP業者收到IP Address，再回傳給瀏覽器(Google Chrome)

4. `瀏覽器收到IP Address後`，就會`發送Request到Google的Server要資料`(HTML、CSS、JavaScript)

5. 瀏覽器收到Google Server回傳的檔案(HTML、CSS、JavaScript)，並顯示在畫面上

## Traceroute

當想要查看`IP經過哪些路由`，可以`透過Traceroute追蹤`，參考下方

```bash
$ traceroute google.com
traceroute to google.com (172.217.24.14), 64 hops max, 52 byte packets
 1  172.20.10.1 (172.20.10.1)  4.699 ms  2.728 ms  2.832 ms
 2  * * *
 ...
10  tsa01s07-in-f14.1e100.net (172.217.24.14)  36.542 ms  29.972 ms  30.579 ms
 ```

看到有些會顯示星號(***)，是因為`沒有在時間內確認封包`，可能是有使用防火牆或是其他安全措施

## 改善WebSite的performance

於瀏覽器中輸入www.google.com，通常都會很快的回覆到瀏覽器上，必須知道有哪些方向可以調整WebSite的performance

1. `Server的位置`，因為網路是由很多電腦所連接的，當`Server位置距離你越進`，則`速度越快`

2. `路程(Trips)`，若沒有經過太多的路由，當然速度會越快

3. `檔案大小`，當HTML、CSS、JavaScript檔案越小，傳輸的速度會越快回到Client上；反之，檔案越大，速度則會變慢


參考資料：

- [Traceroute](https://zh.wikipedia.org/wiki/Traceroute)