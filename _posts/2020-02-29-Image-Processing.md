---
layout: post    
title: 影像處理
date: 2020-02-29 14:10
categories: [ImageProcessing]
---

## 影像基本概念

### 像素
`數位影像是由一粒一粒的像素(Pixel)所組成`，是組成影像的最小元素，`每張數位影像是由不同顏色的像素所組合而成`，而像素數量越多，越能表現影像細節，而`像素數量越多`，`所佔空間也越大`

如下圖，紅色方框處就是一個像素

![pic](https://i.imgur.com/LTrcuER.png)

### 解析度

如果擁有越多像素，畫面細節則越清楚，可以由下圖理解此原理

![pic](https://upload.wikimedia.org/wikipedia/commons/f/f2/Resolution_illustration.png)

當像素為5x5的時候，圖片是非常不清楚的，但像素越來越多到最右方的100x100的時候，可以清楚地顯示「R」

解析度再螢幕以PPI(Pixel Per Inch)為單位，而印刷以DPI(Dot Per Inch)為單位

## 影像種類

1. 點陣圖：以`像素為基礎`組成影像，能真實呈現影像原貌及色彩差異，`放大後會有鋸齒效果`

2. 向量圖：以`數學算式所繪製成的影像`，圖形放大會重新計算，因此`不會有鋸齒狀`

## 影像色彩類型

1. 黑白：只有`黑、白`兩色，`每個像素大小為1Bit`

2. 灰階：還是`黑、白`色，但有`256種明亮度`，`每個像素大小為1Byte`

3. 256色：最多256種顏色，`每個像素大小為1Byte`

4. 高彩：最多65536種顏色，`每個像素大小為2Byte`

5. 全彩：最多1677萬種顏色，`每個像素大小為3Byte`

## What is image processing?

影像處理(image processing)，從實體擷取影像，並對影像進行處理、分析、量測與解譯出相關的資訊

## 影像處理步驟

影像處理步驟可以分為五個，如下圖

![pic](https://i.imgur.com/RVwQcIa.png)

1. 影像擷取(Image Acquisition)：從數位相機、掃描器、X光掃描、雷達...等皆可以得到數位影像

2. 預處理(Preprocessing)：擷取數位影像時，可能受到外在環境(光源、震動...等)影響，導致取得的影像品質不佳，此時就必須透過一些方法對影像做處理，藉此改善影像品質，例如：去除雜訊、增強影像

3. 分割(Segmentation)：將數位影像中的目標物，從原影像分割出來，例如：擷取車牌號碼

4. 表示與描述(representation and description)：圖形識別應用，常會從影像中擷取有用的物件或特徵 

    4-1 表示：用`簡單的表示式`來表示物件，例如：下圖，要`取出網球`這個物件，可以用簡單的圖形(圓形)，來表示這個物件

    4-2 描述：再以`數值`描述物件，例如：下圖，要`取出網球`這個物件，可以將簡單的圖形用數值(圓的半徑)描述出來

    ![pic](https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/Tennis_racket_and_ball.JPG/250px-Tennis_racket_and_ball.JPG)

5. 辨識與解讀(recognition and interpretation)：給予物體不同標示及意義

參考資料：

- [單元一、影像處理基本概念](http://yuan.yocjh.kh.edu.tw/photoimpact/01.htm)

- [解析度到底是什麼？](https://www.viewsonic.com/tw/pr/content/%E8%A7%A3%E6%9E%90%E5%BA%A6%E5%88%B0%E5%BA%95%E6%98%AF%E4%BB%80%E9%BA%BC_7.html)

- [影像處理](https://zh.wikipedia.org/wiki/%E5%9B%BE%E5%83%8F%E5%A4%84%E7%90%86)

- [數位影像處理簡介](http://nova.bime.ntu.edu.tw/~ttlin/Course01/lecture_notes/C1_LECTURE_NOTE_01(2%20in%201).pdf)

- [數位影像處理簡介](http://nova.bime.ntu.edu.tw/~ttlin/Course01/lecture_notes/c1lecture_note01.htm)

- [什麼是影像前處理?](https://smasoft-tech.com/tag/%E5%BD%B1%E5%83%8F%E5%89%8D%E8%99%95%E7%90%86%E3%80%81%E5%BD%B1%E5%83%8F%E9%A0%90%E8%99%95%E7%90%86%E3%80%81%E6%A9%9F%E5%99%A8%E8%A6%96%E8%A6%BA%E3%80%81%E4%BA%8C%E5%80%BC%E5%8C%96%E3%80%81%E5%BD%A2-2/)