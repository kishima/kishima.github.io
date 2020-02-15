---
layout: default
title: "Family mruby"
permalink: /jp/family_mruby/manual/
---

# Family mruby の始め方(v0.6.0)

まだ実行環境の開発中のためファームウェアが色々と未熟ですが、ご容赦ください。
C97で購入された方向けの説明は[こちら](https://kishima.github.io/jp/family_mruby/manual_v97/)です。

---

## 1.必要なもの

* VGAモニタとVGAケーブル（低解像度に対応したもの）
* PS/2キーボード（相性の問題が多いです。特にUSB変換コネクタを使用したものは動かない場合があります）
* 1.5A以上程度供給できるUSB電源
* マイクロUSBケーブル（長すぎないものが良いです）
* GROVEケーブル（Arduino+USBホストシールドと連携する場合）

### 今後対応予定

現在ファームウェアが未対応ですが、以下のパーツも使えるようにする予定です。

* AUXで接続できるアンプ付きスピーカーとAUXケーブル
* マイクロSDカード

---

## 2.基板の組み立て

TMMF2020で配布したセットでははんづけ作業不要です。

---

## 3.基板の説明

基板の各ブロックの説明です。

<img src="/images/Narya2.0_org_mark.jpg" alt="Narya board description">

* USB（実装済み）  
マイクロUSBコネクタです。
電源の供給およびファームウェアの書き換えのために利用します。
* PW（実装済み）  
電源スイッチです。マイクロUSBコネクタ側にスライドさせることでONになります。
* VGA（実装済み）  
VGA映像出力端子です。
* PS/2（実装済み）  
PS/2キーボード入力端子です。
* AUX（実装済み）  
音声出力端子です。
本基板はアンプは搭載していないので、アンプ付きスピーカー等に接続して利用ください。
* RST（実装済み）  
ESP32のENに接続されています。
添付のタクトスイッチをハンダ付けすることでリセットボタンとして利用できます。
* BOOT（未実装）  
ESP32のIO0に接続されています。
通常は使用しません。
* SD（実装済み）  
秋月電子で販売しているマイクロSDカードホルダのDIP化キットに対応したフットプリントになっています。
SDカードの接続対応のファームウェアは現在開発中です（メモリ不足問題あり）。
* UART（実装済み）  
GROVEコネクタを接続します。
電源および信号レベルがESP32準拠の3.3Vであることにご注意ください。
Arduino＋USBホストシールドと連携することで、USBゲームパッド等を利用できます。
* IO35（未実装）  
ESP32のIO35をスイッチとして利用する場合に使用します。
IO35はプルアップされた状態です。

---

## 4.使って見る

### 起動〜メインメニュー

VGAモニタとPS/2キーボードを電源を入れる前に接続しておきます。

USBケーブルを接続して、電源スイッチをONにして起動します。

すると以下のような画面が表示されます。

* Open Editor  
  エディタ画面を開きます。
* Run script  
  未対応です。
* Config  
  解像度設定を行えます。また設定をSPIFFSに保存して、次回起動以降に引き継ぐことができます。
* About Fmrb  
  Family mrubyのバージョン表記と、使用中のメモリリソースを表示します。

### エディタ

* MENU
  * Load demo1  
  デモスクリプトを読み込みます。
  * Load demo2  
  デモスクリプトを読み込みます。
  * Toggle Highlight  
  コードのハイライトのON/OFFを設定します。デフォルトでOFFです。（カーソル位置がずれる等のバグがあるため）
* SAVE  
  編集中のスクリプトをSPIFFSに保存します。（SDカード未対応）
* LOAD  
  SPIFFSからスクリプトを読み込みます。（SDカード未対応）
* RUN  
  編集中のスクリプトを実行します。
* QUIT
  エディタを抜けてメインメニューに戻ります。


### 編集

現在のバージョンでサポートしている機能

* カーソル移動
* 挿入、改行
* バックスペース
* Page up/down
* 一行消し (CTRL-D)


### コンパイルと実行
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　：：
F4（RUN）でバイトコードへのコンパイルと実行を行います。
スクリプト実行中は、低解像度に切り替わります。

例外が発生した場合、その内容を示すメッセージを表示して、エディタ画面に戻ります。

### API

[こちら](https://kishima.github.io/jp/family_mruby/commands/)
を参照ください。

---

## 5.ファームウェアの更新

最新のファームウェアは以下のリポジトリで継続的に更新しています。

[https://github.com/kishima/family_mruby](https://github.com/kishima/family_mruby)

最新版は、[v0.6.0 beta](https://github.com/kishima/family_mruby/releases/tag/0.6.0)です。

esptool.pyを使って、バイナリファイルを書き込む場合、ソースコードのビルドは不要です。
MacやLinuxで書き込む場合のesptool.pyのオプションは、release_bin/flash_bins.sh を参照ください。
Windowsでも、フラッシュツールを使えば書き込めるはずですが、未チェックなので、追って手順を更新したいと思います。

もしビルドして改造等したい場合には、ArduinoIDEではなく、コマンドラインで動かすESP-IDF環境が必要となります。

v0.6.0 betaは、[ESP-IDF v3.2.2](https://docs.espressif.com/projects/esp-idf/en/v3.2.2/get-started/index.html)をインストール済みの環境でReadmeの手順に従ってビルドしてください。

ESP-IDFの環境がそろっていれば、git cloneしてmake menuconfig、make flashするだけなので、ビルドは比較的容易かと思います。

書き込みの際は、基板をPCとUSBケーブルで接続します。
電源スイッチにTPS2065を採用して突入電流を抑えていますが、動作不安定にならないように、開発時は供給電力に余裕のあるUSBポートを使用してください。

---

## 6.その他

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


* PS/2 キーボード

変更無しです。マウスは非対応です。

|Type|Default|
|:---|:------|
|DATA  |GPIO32 |
|CLK   |GPIO33 |

* Audio

変更無しです。

|Type|Default|
|:---|:------|
|Audio  |GPIO25 |

---

### 問い合わせ

Family mrubyのファームウェアに関しては、githubのissueをご利用ください。

その他については以下のメールアドレスを利用ください。

kishima@silentworlds.info

個人の趣味の範囲で運営しているプロジェクトのため、十分な対応を保証することができない点、ご容赦ください。

