---
layout: default
title: "BOOTHでESP32-VGA基板を購入された方へ"
permalink: /jp/narya_2_0/
---

# BOOTHでESP32-VGA基板を購入された方へ

[BOOTHのお店](https://silentworlds.booth.pm/)

## 1. 特徴

* ESP32-WROVER-Bを搭載
* [FabGLライブラリ](http://www.fabglib.org/) を使用することを前提にVGA、PS2などに対応（一部使用しているピンが標準からずれてます）
* FT231XS、TPS2065搭載

## 2. 背景

もともと[Family mrubyプロジェクト](https://kishima.github.io/family_mruby/) 向けに設計していた基板です。Naryaと呼んでいます。
USBキーボード対応のために基板をアップデートしようと考えているため、PS/2キーボード対応の現行基板の在庫を、Family mruby用としてではなく汎用の基板として販売してみることにしました。

## 3. 基板の説明

基板の各ブロックの説明です。

<img src="/images/Narya2.0_org_mark.jpg" alt="Narya board description">

* USB（実装済み）  
マイクロUSBコネクタです。
電源の供給およびファームウェアの書き換えのために利用します。
* PW  
電源スイッチです。マイクロUSBコネクタ側にスライドさせることでONになります。
* VGA  
VGA映像出力端子です。
* PS/2  
PS/2キーボード入力端子です。
* AUX  
音声出力端子です。
本基板はアンプは搭載していないので、アンプ付きスピーカー等に接続して利用ください。
* RST  
ESP32のENに接続されています。
添付のタクトスイッチをハンダ付けすることでリセットボタンとして利用できます。
* BOOT  
ESP32のIO0に接続されています。
通常は使用しません。
* SD  
秋月電子で販売しているマイクロSDカードホルダのDIP化キットに対応したフットプリントになっています。
はんだ付けすることでSDカードを接続できますが、ピンの配置は設計情報参照です。
* UART
GROVEコネクタを接続します。
電源および信号レベルがESP32準拠の3.3Vであることにご注意ください。
* IO35  
ESP32のIO35をスイッチとして利用する場合に使用します。
IO35はプルアップされた状態です。

### スペック

| # | 項目 | スペック |
|:---:|:---|:---|
|1 | マイコン | ESP32（ESP32-WROVER-B） |
|2 | RAM | メイン SRAM(520KB) SPI-SRAM(8MB) |
|3 | 電源 | マイクロUSBより給電(1.5A以上の電源推奨) |
|4 | 外部ストレージ | マイクロSD |
|5 | 映像出力 | VGA（FabGLに準じて解像度が特殊なので映らないモニタもあるかもしれないです） |
|6 | キーボード入力 | PS/2キーボード |
|7 | 音声出力 | モノラルAUX(ファームウェア開発中) |
|8 | 拡張端子 | GROVE 3.3V-UART |
|9 | 無線通信 | ESP32のスペックに準じる |


### ハードウェア設計情報

回路図、ガーバーデータを以下のリポジトリで公開しています。
詳細はこちらを参照ください。

[Narya Board v2.0.0リリース](https://github.com/kishima/narya_board/releases)

3Dプリンタ用基板ケースのデータも公開しています。

### ピン配置

<img src="/images/pinconfig.png" alt="Pin assignment">

### v2.0 (最新)

PCBA量産版。過去にC97、TMMF2020で頒布しました。

<img src="/images/Narya2.0.jpg" alt="Narya基板">

<img src="/images/narya_2.0.jpg" alt="Narya基板（スルーホール部品はんだ付け前）">


### 組み立ての注意点

はんだ付けの順番は特に指定はないですが、背が低い部品からはんだ付けするのが良いと思います。

金属部分が厚い部分はしっかりと熱して接触不良を起こさないようにはんだ付けしてください。

SDカードをはんだ付けするのが一番面倒かと思うので、まずピンの位置をあわせてからはんだ付けするようにしてください。
支え用のピンは2.54の穴に合わせてください。

<img src="/images/pins.jpg" alt="SDカード基板用のピンは写真のように折って使ってください">

<img src="/images/soldered.jpg" alt="Narya基板（スルーホール部品はんだ付け後）">

### ケース付きの場合

ケースが付いている場合に、ケースの蓋を閉じるには接着剤を用いて下さい。

<img src="/images/case.jpg" alt="ケースの蓋を閉じた状態">

### 参考書籍

基板の設計するなかで得た知見を同人誌にまとめました。

**「ゼロから始めるmrubyデバイス作り」** （[BOOTHの販売ページへ](https://silentworlds.booth.pm/items/1564678)）


## 4. 使い方

### FabGL基板として使用する場合の注意点

ファームウェアを上書きすると、FabGLを動かすためのESP32開発基板としても用いることができます。

Narya基板を、素のFabGLと組み合わせて用いる場合、VGAのVSyncが標準のピン配置とことなる接続をしているため、注意が必要です。

* VGAの端子

VSyncのみ変更されています。ご注意ください。

|Type|Default|Family mruby|
|:---|:------|:-----------|
|Red1  |GPIO22 |GPIO22 |
|Red0  |GPIO21 |GPIO21 |
|Green1|GPIO19 |GPIO19 |
|Green0|GPIO18 |GPIO18 |
|Blue1 |GPIO5  |GPIO5  |
|Blue0 |GPIO4  |GPIO4  |
|HSync |GPIO23 |GPIO23 |
|VSync |GPIO15 |GPIO27 |

設定例

```
VGAController.begin(GPIO_NUM_22, GPIO_NUM_21, GPIO_NUM_19, GPIO_NUM_18, GPIO_NUM_5, GPIO_NUM_4, GPIO_NUM_23, GPIO_NUM_27);
```

注意点：FabGLの最新版で一部映像出力されないサンプルがあったので、調査中です(2022/2/1)。

* PS/2 キーボード

変更無しです。ポートが１つしかないのでマウスと同時には使えないです。

|Type|Default|
|:---|:------|
|DATA  |GPIO32 |
|CLK   |GPIO33 |

* Audio

変更無しです。

|Type|Default|
|:---|:------|
|Audio  |GPIO25 |

### Family mruby 基板として利用する場合

こちら参照。
https://kishima.github.io/family_mruby/

