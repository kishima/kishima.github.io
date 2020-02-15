---
layout: default
title: "Family mruby API reference"
permalink: /jp/family_mruby/commands/
---

# コマンドリファレンス(Family mruby ver 0.6.0)

## Narya::Display モジュール

画面表示に関する機能を扱います。

### モジュールメソッド

#### clear

* 引数: なし

画面を黒１色で塗りつぶします。

#### draw_pixel

 * 引数: x,y,r,color1,color2
   * x: X座標
   * y: Y座標
   * r: 半径
   * color1: 描画色

点を描画します。

#### draw_line

 * 引数: x1,y1,x2,y2,color1
   * x1: 始点のX座標
   * y1: 始点のY座標
   * x2: 終点のX座標
   * y2: 終点のY座標
   * color1: 描画色

線を描画します。

#### draw_rect

 * 引数: x1,y1,x2,y2,color1,color2
   * x1: 始点のX座標
   * y1: 始点のY座標
   * x2: 終点のX座標
   * y2: 終点のY座標
   * color1: 枠の描画色
   * color2: 塗りつぶしの描画色（省略可）

矩形を描画します。

#### draw_circle

* 引数: x,y,r,color1,color2
  * x: X座標
  * y: Y座標
  * r: 半径
  * color1: 描画色
  * color2: 背景色（省略可）

円を描画します。

#### draw_text

 * 引数: x,y,text,color1,color2
   * x: X座標
   * y: Y座標
   * text: 描画文字列
   * color1: 文字色
   * color2: 背景色（省略可）

テキストを描画します。

#### draw_picture

 * 引数: x,y,path
   * x: 起点のX座標
   * y: 起点のY座標
   * path: 画像ファイルのパス
    
画像ファイルを読み込み、スクリーンに描画します。


#### width

* 引数: なし

スクリーン幅のピクセル数を返します。

#### height

* 引数: なし

スクリーン高さのピクセル数を返します。

#### double_buffered?

* 引数: なし

ダブルバッファが有効かどうかをtrue/falseで返します。

#### swap

* 引数: なし

描画結果を画面に反映します。

## Narya::Bitmap クラス

### インスタンスメソッド

#### load

 * 引数: path
   * path: 画像ファイルのパス

画像ファイルを読み込み、内部のメモリに格納します。

#### draw

 * 引数: x,y
   * x: 起点のX座標
   * y: 起点のY座標

格納されている画像データを指定の位置に描画します。

## Narya::Sprite クラス

### インスタンスメソッド

#### initialize

 * 引数:

#### move_to

 * 引数: x,y
   * x: X座標
   * y: Y座標

指定の位置にスプライトを移動させます。

#### move

  * 引数: x,y
    * x: X座標の移動量
    * y: Y座標の移動量

スプライトの現在位置から指定のピクセル数分だけシフトさせます。

## Narya::Input モジュール

### モジュールメソッド

#### available

* 引数: なし

有効なキー入力があるかどうかをtrueまたはfalseで返します。

#### keydown?

* 引数: key_code
   * Key_code: キーコード（Fixnum）

有効なキー入力があるかどうかをtrueまたはfalseで返します。

例：

```
Narya::Input::keydown?(Narya::Key::K_a)
```

#### get_key

* 引数: なし

入力されたキーコードを返します。

#### paddown?

* 引数: pad_code
  * pad_code: パッドコード(Fixnum)

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

Family mrubyのバージョン（文字列）を取得します。

#### narya_ver

* 引数: なし

mruby-esp32-naryaのバージョン（文字列）を取得します。

