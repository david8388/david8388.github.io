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

## 重啟已經停止的 container

首先啟動 busybox 這個 container

```shell
$ docker run busybox echo hi there
hi there
```

顯示 container 狀態

```shell
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
ca48fa2ca229        busybox             "echo hi there"     46 seconds ago      Exited (0) 45 seconds ago
```

`找到需要重啟的container ID`，執行`docker start -a targetContainerID`

```shell
$ docker start -a ca48fa2ca229
hi there
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
ca48fa2ca229        busybox             "echo hi there"     9 minutes ago       Exited (0) 5 seconds ago
```

## 移除已經停止的 container

執行時會再確認是否要執行，若確認執行 key y 否則為 N

```shell
$ docker system prune
WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all dangling images
        - all dangling build cache
Are you sure you want to continue? [y/N] y
Deleted Containers:
ca48fa2ca229f6cb0d33de1b9475a9825772f532625b27d46cc8d35d40178911
.....
```

註：執行完此指令，cache 裡面的 container 就會被移除，也就是需要重新下載 Image 到 local 端

## 取得 Log

可以在執行的時候，透過`docker start -a ContainerID` or `docker run ImageName`，取得 Log

但有可能紀錄已經清掉，就沒辦法拉回去看，這時候可以使用`docker logs containerID`取得 Log

```shell
$ docker create busybox echo hi there
cc5219c519b3e2b32055f1c1e520e98ce7bb71cf0c7f097b334a310581c66693
$ ocker start cc5219c519b3e2b32055f1c1e520e98ce7bb71cf0c7f097b334a310581c66693
cc5219c519b3e2b32055f1c1e520e98ce7bb71cf0c7f097b334a310581c66693
$ docker logs cc5219c519b3e2b32055f1c1e520e98ce7bb71cf0c7f097b334a310581c66693
hi there
```

## 終止 Container

有兩種方式可以停止 container：

1. docker stop containerId
2. docker kill containerId

先建立並執行一個 Image

```shell
$ docker create busybox ping google.com
ea984dfb57b3ad0a5d12e9378022d7e048c7929c2b6e73f28f8f85f9e108360b
$ docker start ea984dfb57b3ad0a5d12e9378022d7e048c7929c2b6e73f28f8f85f9e108360b
ea984dfb57b3ad0a5d12e9378022d7e048c7929c2b6e73f28f8f85f9e108360b
$ docker logs ea984dfb57b3ad0a5d12e9378022d7e048c7929c2b6e73f28f8f85f9e108360b
PING google.com (216.58.200.238): 56 data bytes
64 bytes from 216.58.200.238: seq=1 ttl=37 time=106.250 ms
...
```

```shell
$ docker stop ea984dfb57b3
ea984dfb57b3
$ docker kill ea984dfb57b3
ea984dfb57b3
```

## `stop vs kill`

stop：會先發送 SIGTERM 的 message，10 秒後在發送 SIGKILL 的 message。Docker 內部應用程序接收 SIGTERM 的 message，做退出前工作，e.g：保存狀態 或 處理當前請求

kill：發送 SIGKILL 的 message，應用程式直接退出

參考資料：

-[淺談輕量化的虛擬技術 - Docker 容器](http://www.cc.ntu.edu.tw/chinese/epaper/0036/20160321_3611.html)

-[初探容器技術(Container)](https://blog.yowko.com/container/)

-[docker stop 与 docker kill 的区别](https://www.cnblogs.com/zhenyuyaodidiao/p/5283593.html)
