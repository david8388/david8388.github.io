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

## 找出所有在運行的 Container

先執行 busy box 這個 image

```shell
$ docker run busybox ping google.com
PING google.com (172.217.160.78): 56 data bytes
64 bytes from 172.217.160.78: seq=0 ttl=37 time=10.463 ms
.....
```

`docker ps 找出正在運行的 container`

```shell
$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
f963d05ef82b        busybox             "ping google.com"   7 seconds ago       Up 7 seconds                            eloquent_stallman

```

`docker ps -a：取得所有的 container(正在運行或已經結束)`

```shell
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
f963d05ef82b        busybox             "ping google.com"   5 minutes ago       Exited (0) 4 minutes ago                        eloquent_stallman
4e04afc1d754        busybox             "ls"                6 minutes ago       Exited (0) 6 minutes ago                        goofy_diffie
b289a5def619        busybox             "ls"                12 minutes ago      Exited (0) 12 minutes ago                       keen_tesla
e006690afb33        hello-world         "/hello"            13 minutes ago      Exited (0) 13 minutes ago                       hungry_dubinsky
29356ad8021a        hello-world         "/hello"            24 hours ago        Exited (0) 24 hours ago                         stoic_feistel
cbb8cb63ff1f        hello-world         "/hello"            24 hours ago        Exited (0) 24 hours ago                         angry_gauss

```

## Container 的 LifeCycle

docker run = docker create + docker start

```shell
$ docker create hello-world
009771fd1eab83c70da8587f629fb15a125d2a60a0fab29ba5ac9d72966b0acf

$ docker start -a 009771fd1eab83c70da8587f629fb15a125d2a60a0fab29ba5ac9d72966b0acf

Hello from Docker!
...
```

docker start -a，`-a`表示附加所有訊息並且 output 到 terminal 上

參考資料：

-[淺談輕量化的虛擬技術 - Docker 容器](http://www.cc.ntu.edu.tw/chinese/epaper/0036/20160321_3611.html)

-[初探容器技術(Container)](https://blog.yowko.com/container/)
