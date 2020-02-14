---
layout: default
title: "Family mruby API reference"
permalink: /jp/family_mruby/commands_v050/
---

# コマンドリファレンス(Family mruby ver 0.5.0)

## Narya::Display モジュール

画面表示に関する機能を扱います。

### Module methods

#### clear

* 引数
  * なし

画面を１色で塗りつぶします。

#### draw_circle

* 引数
  * x,y,r,color
    * x: X座標
    * y: Y座標
    * r: 半径
    * color: 描画色

円を描画します。

#### draw_text

  * x,y,text
    * x: X座標
    * y: Y座標
    * text: 描画文字列

テキストを描画します。

#### swap

* 引数
  * なし

描画結果を画面に反映します。

## Narya::Input モジュール

#### available

* 引数
  * なし

有効なキー入力があるかどうかをtrueまたはfalseで返します。

#### keydown?

* 引数
  * キーコード(整数)

有効なキー入力があるかどうかをtrueまたはfalseで返します。

## Narya::Sprite モジュール

開発中です。

## Narya::Strage モジュール

開発中です。

## Narya::Sound モジュール

開発中です。

## Narya::Font モジュール

開発中です。

## Narya::Image モジュール

開発中です。


## キーコード

* 144 RETURN
* 151 UP
* 153 DOWN
* 155 LEFT
* 157 RIGHT
