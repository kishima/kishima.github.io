---
layout: default
title: "Family mruby"
permalink: /jp/family_mruby/
---

# Family mruby

## Family mrubyとは

### 特徴

* PCいらずでRubyのコードを実行

### デモ映像

<iframe width="560" height="315" src="https://www.youtube.com/embed/za9LFTUpPRg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Narya基板

### スペック

| # | 項目 | スペック |
|:---:|:---|:---|
|1 | マイコン | ESP32（ESP32-WROVER-B） |
|2 | RAM | メイン SRAM(520KB) SPI-SRAM(8MB) |
|3 | 電源 | マイクロUSBより給電 |
|4 | 外部ストレージ | マイクロSD(ファームウェア開発中) |
|5 | 映像出力 | VGA（対応解像度(TBD)） |
|6 | キーボード入力 | PS/2キーボード |
|7 | 音声出力 | モノラルAUX(ファームウェア開発中) |
|8 | 拡張端子 | GROVEコネクタ(3.3V-UART)(5Vに更新予定)(ファームウェア開発中) |


### 設計情報

[https://github.com/kishima/mruby-esp32-narya](https://github.com/kishima/mruby-esp32-narya)

### v2.0 (最新)

PCBA量産版。C97で頒布。

変更点

* UART通信状態表示のLEDの回路図ミスを修正
* 電源LEDのソースを電源スイッチ後段に変更

<img src="/images/Narya2.0.jpg" alt="Family mruby demo">

### v1.4

変更点

* 量産向けに基板外形、アートワークを見直し
* UART接続を想定して、GROVEコネクタを追加
* 電源スイッチ追加

### v1.3

変更点

* FT231XのGND未接続ピンを修正

### v1.2

「ゼロから始めるmrubyデバイス作り」で参照。技術書典7で基板のみ頒布。

<img src="/images/2nd.jpg" alt="Family mruby demo">

### v1.0

初期試作基板。色々間違いあり。

<img src="/images/1st.jpg" alt="Family mruby demo">

