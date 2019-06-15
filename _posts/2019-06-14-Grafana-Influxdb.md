---
layout: post
title: 使用Grafana 呈現圖形化資料
date: 2019-06-14 22:00
categories: [Grafana, InfluxDB]
---

## Outline

使用 Grafana 連接 InfluxDB，呈現圖形化分析數據

## What is Grafana & InfluxDB?

Grafana 是一個監控、分析數據，將資料圖形化的平台

InfluxDB 是一個時序型(Time Series)的開源資料庫，廣泛用於儲存系統監控數據

## 在 mac 安裝 Grafana

```shell
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" // 使用Homebrew安裝，若電腦已經有Homebrew，則可以略過
$ brew install grafana

// 安裝完成後的訊息
To have launchd start grafana now and restart at login:
  brew services start grafana
Or, if you dont want/need a background service you can just run:
  grafana-server --config=/usr/local/etc/grafana/grafana.ini --homepath /usr/local/share/grafana --packaging=brew cfg:default.paths.logs=/usr/local/var/log/grafana cfg:default.paths.data=/usr/local/var/lib/grafana cfg:default.paths.plugins=/usr/local/var/lib/grafana/plugins

$ brew install influxdb

// 安裝完後的訊息
To have launchd start influxdb now and restart at login:
  brew services start influxdb
Or, if you dont want/need a background service you can just run:
  influxd -config /usr/local/etc/influxdb.conf
```

## InfluxDB 建立 Database 及 User

```shell
$ influx
Connected to http://localhost:8086 version v1.7.6
InfluxDB shell version: v1.7.6
Enter an InfluxQL query
> create user admin with password 'adminpass' with all privileges  // 建立帳號 admin, 密碼 adminpass ：擁有最高權限
```

`InfluxDB Config located at /usr/local/etc/influxdb.conf`

## 修改 InfluxDB Config and restart

```shell
[http]
  # Determines whether user authentication is enabled over HTTP/HTTPS.
  # auth-enabled = true //預設為false, 改為true
```

## 首先啟動 Grafana 及 influxDB

```shell
$ sudo brew services start grafana
$ sudo brew services start influxdb
$ sudo brew services stop grafana  // 這是中止Grafana服務的script
$ sudo brew services stop influxdb // 這是中止InfluxDB服務的script
```

`Grafana 預設網址為http://127.0.0.1:3000`

## 開啟 Grafana

![View](https://i.imgur.com/3BD4I8Q.png)

預設帳號、密碼皆為 admin，登入之後會確認是否需要調整

## 新增資料來源

點擊畫面中 Add data source

![View](https://i.imgur.com/kbzjsQc.png)

選擇 InfluxDB

![View](https://i.imgur.com/q7qpSwU.png)

填入基本資訊，並儲存測試
![View](https://i.imgur.com/LhgncHt.png)

## 新增 Dashboard

![View](https://i.imgur.com/LluGNGb.png)

選擇 Choose Visualization
![View](https://i.imgur.com/kL8UQoZ.png)

有許多視覺化圖形可供選擇
![View](https://i.imgur.com/3ngctRk.png)

## DashBoard 畫面

Panel 的大小都可以透過拖拉方式做調整，也可以透過新增 Visualization 的方式增加資料的呈現

![View](https://i.imgur.com/RJcv9A1.png)

參考資料

- [Homebrew](https://brew.sh/index_zh-tw)

- [Download Grafana](https://grafana.com/grafana/download)

- [使用 influxdb + telegraf + grafana 收集主機資料、監控，並圖形化分析](https://ssorc.tw/7306)
