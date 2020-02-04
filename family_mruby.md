---
layout: default
title: "Family mruby"
permalink: /family_mruby/
---

[Japanese](https://kishima.github.io/jp/family_mruby/)

# Family mruby

---

<img src="/images/topimage.png" alt="Family mruby logo">

## What is Family mruby

In 80s, BASIC was one of the famous languages for children to learn programing at first.
A computer for consumers has limited resource to run any programing language, however there are some other good machines like MSX, Family basic on Family Computer in Japan. I think many senior programmers learnt the fun of programming.

Today we can enjoy most of all programming language in free of charge. I think however it might be too complicated to begin the first step of learning programming language since it's difficult to prepare proper condition to making what they want like a game application after a "Hello World".

Then I decided to create a small computer that anybody can make a simple game with a script language. This is the "Family mruby".

Family mruby is a stand-alone development environment based on an original PCB, which can edit and execute Ruby code with a VGA display and a PS/2 keyboard.
You can enjoy Ruby programming without a PC to send code to the board.

(Remark: Now development of firmware is ongoing, PC is needed when you update the firmware.)

Family mruby has following properties.

* Enabling stand-alone Ruby environment using mruby.
* Editing and compiling code is done on the PCB.
* Enabling to utilize VGA signal output and PS/2 keyboard input without any additional IC（Thanks to [FabGL](https://github.com/fdivitto/FabGL)）
* Supporting Micro SD card and AUX output. (developing)


### Demonstration

Following video shows to edit Ruby code and execute it.

<div class="movie-wrap">
<iframe width="560" height="315" src="https://www.youtube.com/embed/za9LFTUpPRg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

.

---

## How to use it?

[Preparing...](https://kishima.github.io/jp/family_mruby/manual/)


---

## Architecture

<img src="/images/family-mruby-arch.jpg" alt="Family mruby architecture">

---

## Firmware

Latest release is v0.5 beta.

https://github.com/kishima/family_mruby

---

## Narya Board

Family mruby is running on the Narya board.

I published a private technical book to explain how to design the board.

**「ゼロから始めるmrubyデバイス作り」** （[BOOTH web site](https://silentworlds.booth.pm/items/1564678)）

### HW specification

| # | items | explanation |
|:---:|:---|:---|
|1 | Micro processor | ESP32（ESP32-WROVER-B） |
|2 | RAM | Main SRAM(520KB) SPI-SRAM(8MB) |
|3 | Power supply | Using micro USB(1.5A is recommended) |
|4 | External Strage | Micro SD(developing) |
|5 | Video output | VGA（Supported resolution:TBD） |
|6 | Key input | PS/2 keyboard |
|7 | Audio output | mono-AUX(deloping) |
|8 | Additional IO | GROVE 3.3V-UART (developing) |
|9 | WiFi | See ESP32 spec |


### HW design

Schematics and gerber data is shared in the following github repository.

[https://github.com/kishima/narya_board](https://github.com/kishima/narya_board)


### Pin assignment

<img src="/images/pinconfig.png" alt="Pin assignment">

### v2.0 (Latest)

Build by Elecrow PCBA. Released on C97.

Changes

* Fix error of schimatics related to LEDs.
* Changed the LED position to show power input.

<img src="/images/Narya2.0.jpg" alt="Narya board v2.0">

<img src="/images/narya_board_with_case.jpg" alt="Narya board v2.0 with a case">

### v1.4

Chanages

* Update design for PCBA.
* Add GROVE connecter
* Add power switch

### v1.3

Changes

* Fix an issue of floating GND of FT231X

### v1.2

Released in Techbook Fest #7. Reference of 「ゼロから始めるmrubyデバイス作り」

<img src="/images/2nd.jpg" alt="Family mruby demo">

### v1.0

SFirst prototype. Some errors.

<img src="/images/1st.jpg" alt="Family mruby demo">

