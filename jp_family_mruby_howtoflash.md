---
layout: default
title: "How to flash Family mruby"
permalink: /jp/family_mruby/how_to_flash/
---

# Family mruby ファームウェア更新方法

## Macの場合

esptool.pyを利用して、USBシリアル通信を介して、バイナリファイルを書き込みます。

### USBシリアル通信ドライバの確認

基板をPCに接続して、以下のコマンドを実行した結果を確かめてください。

```
$ ls /dev/
```

`cu.usbserial-***`という名前が見つかれば、通信可能な状態です。

見つからない場合は、以下の手順でドライバをインストールしてください。

### USBシリアル通信ドライバのインストール

Narya基板では、USBシリアル変換のために、FTDI社のチップを使用しています。

https://www.ftdichip.com/Drivers/VCP.htm

こちらから、Max OS X の該当するドライバをダウンロードします。
あとは、解凍してインストールするだけです。
詳細は以下のスイッチサイエンスさんの説明が参考になると思います。

https://mag.switch-science.com/2013/01/23/install_vcp_driver_to_mac/
　

### ESP-IDFのインストール

https://docs.espressif.com/projects/esp-idf/en/v3.2.2/get-started/index.html

こちらの内容に従って作業します。
簡単に、日本語での説明を以下にまとめています。

* `sudo easy_install pip` を実行
* https://dl.espressif.com/dl/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz をダウンロードする
* ダウンロードしたファイルを展開する

```
mkdir -p ~/esp
cd ~/esp
tar -xzf ~/Downloads/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz
```

* `~/.profile`に以下の2行を追加する

```
export PATH=$HOME/esp/xtensa-esp32-elf/bin:$PATH
export IDF_PATH=~/esp/esp-idf
```

設定が終わったら一度ターミナルを再起動させてください。

（バイナリのソフトを書き込むだけであれば、ツールチェインのインストールは省略可能です）

* githubからESP-IDFをダウンロードします

```
cd ~/esp
git clone -b v3.2.2 --recursive https://github.com/espressif/esp-idf.git
```

* Pythonのパッケージのインストール

```
python -m pip install --user -r $IDF_PATH/requirements.txt
```

以上の作業が終われば、Family mrubyのファームウェアの書き込みとビルド環境が整います。

* Family mrubyリポジトリのクローン

適当な作業フォルダにリポジトリをクローンします。ここでは仮に”work”を作業フォルダにします。

```
cd ~/work
git clone https://github.com/kishima/family_mruby.git
```

* 書き込みの実行

以下のコマンドで、書き込みを実行します。基板を電源を入れた状態で接続しておいてください。

```
cd ~/work/family_mruby/release_bin
unzip family_mruby_bin.zip
./flash_bins.sh /dev/cu.usbserial-****
```

***はデバイスによって異なります。


## Windowsの場合

準備中


## 共通の注意点

### 供給電力

書き込みの際は、基板をPCとUSBケーブルで接続します。
電源スイッチにTPS2065を採用して突入電流を抑えていますが、動作不安定にならないように、開発時は供給可能電力に余裕のあるUSBポートを使用してください。

電力が不足していると、Flashメモリ書き込み中に電圧が落ちて処理が止まり、Flashメモリが破損してしまうこともありえます。
