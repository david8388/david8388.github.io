---
layout: post
title: Docker 介紹
date: 2019-06-15 15:20
categories: [Docker]
---

## What is Docker ?

Docker 是一個圍繞建立、執行 Container 的平台或生態系統

基本概念

Image：唯獨映像檔，擁有執行程式所需的依賴及配置，用來建立 Container

Container：Image 的實例

Repository：image 的儲存庫，例如：[Docker Hub](https://hub.docker.com/)

## Why use Docker ?

Docker 讓安裝、執行軟體變得更簡單，不用再擔心設定及依賴的問題

## 安裝 Docker

筆者環境為 mac，故提供安裝於 [Mac](https://docs.docker.com/docker-for-mac/install/)的 link

## 使用 docker CLI

```shell
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete ...
```

Docker Server 會查詢 `Image cache 是否有 hello-world 這個 image`，若`沒有則會從 Docker Hub 下載`

所以跑第二次 docker run hello-world，因為 Image cache 已經有`hello-world`這個 image，所以不會再從 Docker Hub 下載

```shell
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

參考資料：

-[淺談輕量化的虛擬技術 - Docker 容器](http://www.cc.ntu.edu.tw/chinese/epaper/0036/20160321_3611.html)

-[初探容器技術(Container)](https://blog.yowko.com/container/)
