---
layout: post
title: 利用SSH遠端連線至Ubuntu
date: 2019-12-08 16:45
categories: [Linux, Ubuntu, ssh]
---
 
## What is SSH?
Secure Shell（安全外殼協議），根據Wiki的說法：【 是一種加密的傳輸協定，可以再不安全的網路中為網路服務提供安全的傳輸環境，`SSH最常用的用途是遠端登入系統`】

缺點是沒有GUI介面進行操作，必須使用CMD來達成指令

## 安裝 openssh-client、openssh-server 

openssh-client：使用SSH連接至遠端機器(Ubuntu預設有安裝)

openssh-server：本機開放SSH服務提供外部機器連接


```bash
# install openssh-client

$ sudo apt-get install openssh-client 

# install openssh-server

$ sudo apt-get install openssh-server
```

確認安裝資訊

```bash
$ dpkg -l | grep ssh
```

![pic](https://i.imgur.com/VYWERVS.png)

開放SSH Server 服務，若有看見sshd，代表ssh server服務已經啟用

```bash
$ sudo service ssh start

# 確認ssh-server 是否啟動
$ ps -e | grep ssh
  1331 ?        00:00:00 ssh-agent
  3899 ?        00:00:00 sshd
```

## 登入遠端SSH主機

本機使用SSH服務登入遠端Linux主機，順利登入遠端主機後，若要離開遠端主機，輸入`exit`即可退出

```bash
# username 用戶名稱 及 serverip  主機IP
$ ssh username@serverip
```

![pic](https://i.imgur.com/LycakxN.png)

參考資料：

- [Secure Shell](https://zh.wikipedia.org/wiki/Secure_Shell)

- [[Linux系統] ubuntu利用SSH安全加密連線遠程登錄](https://andy6804tw.github.io/2019/01/23/ubuntu-ssh-remote/)
