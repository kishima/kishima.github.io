---
layout: default
title: "Family mruby API reference"
permalink: /jp/family_mruby/commands/
---

# コマンドリファレンス(Family mruby ver 0.6.0)

## 色の表現方法

各メソッドに渡す色はRGBに対応する３桁の数字の文字列で表現します。

例：

```
Narya::Display::draw_pixel(10,20,"300")
```

"300"の部分が色を表します。
Red,Green,Blueの順に値をセットします。
Family mrubyでは64色(=4の3乗)描画に対応しているので、RGBそれぞれの取りうる値の範囲は0〜3です。
例えば、"300"であれば、R=3、G=0、B=0なので、赤色を表します。
フォーマットに合わない文字列を設定した場合、


### 定義済み色名

数字の代わりに以下の文字列も色として設定できます。すべて大文字で指定してください。

 * "BLACK"
 * "RED"
 * "GREEN"
 * "YELLOW"
 * "BLUE"
 * "MAGENTA"
 * "CYAN"
 * "WHITE"

## Narya::Display モジュール

画面表示に関する機能を扱います。

### モジュールメソッド

#### clear

* 引数: なし
  戻値: self

画面を黒１色で塗りつぶします。

#### draw_pixel

 * 引数: x,y,color
   * x: X座標
   * y: Y座標
   * color: 描画色
 * 戻値: self

点を描画します。

#### draw_line

 * 引数: x1,y1,x2,y2,color1
   * x1: 始点のX座標
   * y1: 始点のY座標
   * x2: 終点のX座標
   * y2: 終点のY座標
   * color1: 描画色
 * 戻値: self

線を描画します。

#### draw_rect

 * 引数: x1,y1,x2,y2,color1,color2
   * x1: 始点のX座標
   * y1: 始点のY座標
   * x2: 終点のX座標
   * y2: 終点のY座標
   * color1: 枠の描画色
   * color2: 塗りつぶしの描画色（省略可）
 * 戻値: self

矩形を描画します。

#### draw_circle

* 引数: x,y,r,color1,color2
  * x: X座標
  * y: Y座標
  * r: 半径
  * color1: 描画色
  * color2: 背景色（省略可）
 * 戻値: self

円を描画します。

#### draw_text

 * 引数: x,y,text,color1,color2
   * x: X座標
   * y: Y座標
   * text: 描画文字列
   * color1: 文字色
   * color2: 背景色（省略可）
 * 戻値: self

テキストを描画します。

#### draw_picture

 * 引数: x,y,path
   * x: 起点のX座標
   * y: 起点のY座標
   * path: 画像ファイルのパス
 * 戻値: self
 
画像ファイルを読み込み、スクリーンに描画します。


#### width

* 引数: なし
* 戻値: Fixnum

スクリーン幅のピクセル数を返します。

#### height

* 引数: なし
* 戻値: Fixnum

スクリーン高さのピクセル数を返します。

#### double_buffered?

* 引数: なし
* 戻値: bool

ダブルバッファが有効かどうかをtrue/falseで返します。

#### swap

* 引数: なし
* 戻値: self

描画結果を画面に反映します。

## Narya::Bitmap クラス

### インスタンスメソッド

#### load

 * 引数: path
   * path: 画像ファイルのパス
 * 戻値: self

画像ファイルを読み込み、内部のメモリに格納します。

#### draw

 * 引数: x,y
   * x: 起点のX座標
   * y: 起点のY座標
 * 戻値: self

格納されている画像データを指定の位置に描画します。

## Narya::Sprite クラス

### インスタンスメソッド

#### initialize

 * 引数:

#### move_to

 * 引数: x,y
   * x: X座標
   * y: Y座標
 * 戻値: self

指定の位置にスプライトを移動させます。

#### move

  * 引数: x,y
    * x: X座標の移動量
    * y: Y座標の移動量
  * 戻値: self

スプライトの現在位置から指定のピクセル数分だけシフトさせます。

## Narya::Input モジュール

### モジュールメソッド

#### available

* 引数: なし
* 戻値: bool

有効なキー入力があるかどうかをtrueまたはfalseで返します。

#### keydown?

* 引数: key_code
   * Key_code: キーコード（Fixnum）
* 戻値: bool

有効なキー入力があるかどうかをtrueまたはfalseで返します。

例：

```
Narya::Input::keydown?(Narya::Key::K_a)
```

#### get_key

* 引数: なし
* 戻値: Fixnum

入力されたキーコードを返します。

#### paddown?

* 引数: pad_code
  * pad_code: パッドコード(Fixnum)
* 戻値: bool

有効なUSBパッド入力があるかどうかをtrueまたはfalseで返します。

## Narya::Storage モジュール

開発中です。

## Narya::Sound モジュール

開発中です。

## Narya::Font モジュール

開発中です。



## Narya:：Keyモジュール

キー入力を識別するためのキーコードの定義です。
[こちら](https://github.com/kishima/mruby-esp32-narya/blob/master/mrblib/mrb_narya.rb) 参照。

## Narya:：Padモジュール

USBゲームパッド入力を識別するためのキーコードの定義です。
[こちら](https://github.com/kishima/mruby-esp32-narya/blob/master/mrblib/mrb_narya.rb) 参照。

## Narya:：Configモジュール

### モジュールメソッド

#### firmware_ver

* 引数: なし
* 戻値: String

Family mrubyのバージョン（文字列）を取得します。

#### narya_ver

* 引数: なし
* 戻値: String

mruby-esp32-naryaのバージョン（文字列）を取得します。

## ESP32::Systemモジュール

### モジュールメソッド

#### delay

 * 引数: time
   * time: 停止時間(msec)
 * 戻値: self

処理を一定時間止めます。内部では、vTaskDelay()が実行されます。

#### tick_ms

 * 引数: なし
 * 戻値: Fixnum

起動してからの経過時間(msec)を返します。
