---
layout: default
title: "Family mruby"
permalink: /jp/family_mruby/
---

# Family mruby

---

## Family mrubyとは

今は昔、子供が最初に触れるプログラミング言語といえば、BASICという時代がありました。
制約は多いですが、パソコン以外にも、MSXやファミコンでBASICができるFamily BASICという製品もあり、そこからプログラミングの面白さを知り、プログラマーになった方もたくさん居られると思います。

そして現在は無料で大抵のプログラミング言語の開発環境はパソコンにインストールすることができる時代になりましたが、できることが多すぎて何をしたらよいのかわからなかったり、Hello Worldの先のゲームを作ったりするまでの環境構築ハードルが高かったり、するような気がしています。

そこで、マイコン一つでちょっとしたゲームをスクリプト言語で作れる環境を作ってみたい、と思って開発したのが、Family mrubyです。

Family mruby はオリジナルのマイコンボードに、VGAディスプレイとPS/2キーボードを接続して、Rubyのコードを書いて実行できる環境です。
パソコンを準備してコードを転送したりするような手間も不要で簡単に楽しめます。

（※現在、ファームウェアが開発中のため、ファームウェア更新の際はPCが必要になります）

以下のような特徴をもっています。

* mrubyを利用することで、PCいらずでRubyのコードを実行
* ソースコードの編集＆コンパイルもマイコン上で実行可能
* ICを追加せずに、VGAモニタ、PS/2キーボードとの接続を実現（[FabGL](https://github.com/fdivitto/FabGL)のおかげです）
* SDカードスロット、AUX端子付き（mrubyから使えるようにする処理は現在開発中）

### デモ映像

Rubyのコードを編集して、コンパイルから実行を行っています。

<iframe width="560" height="315" src="https://www.youtube.com/embed/za9LFTUpPRg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

.

---

## 使い方

[こちらのページ](https://kishima.github.io/jp/family_mruby/manual/)を参照ください。


---

## Narya基板について

Family mruby用の基板（Narya基板と呼びます）の情報です。

基板の設計するなかで得た知見を同人誌にまとめました。

**「ゼロから始めるmrubyデバイス作り」** （[BOOTHの販売ページへ](https://silentworlds.booth.pm/items/1564678)）

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
|8 | 拡張端子 | GROVE 3.3V-UART (5Vに更新予定)(ファームウェア開発中) |
|9 | 無線通信 | ESP32のスペックに準じる |


### HW設計情報

回路図、ガーバーデータを以下のリポジトリで公開しています。

[https://github.com/kishima/narya_board](https://github.com/kishima/narya_board)

3Dプリンタ用基板ケースのデータも公開しています（予定）。

### ピン配置

<img src="/images/pinconfig.png" alt="Pin assignment">

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

