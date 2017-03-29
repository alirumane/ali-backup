---
layout: post
title: Installing NOOBS OS on Raspberry Pi
tags: [Raspberry Pi, NOOBS]
---
>You bought a Raspberry Pi and want to run an OS on it

**N**ew **O**ut **O**f the **B**ox **S**oftware - an easy Operating System installer

Raspberrypi.org suggests NOOBS OS installation. It has complete guide for installing the OS, still cut through...

## A. Setting up

**Essentials:**

* Raspberry Pi
* SD Card (16GB class 10 Preferred / 8GB Class 4 may also work)
* HDMI to VGA/HDMI cable (connecting to Display e.g. Monitor or T.V.)
* Keyboard and Mouse
* Power Supply (Micro USB e.g. phone charger)

## B. Installation

**Instructions**

* Download NOOBS from [https://www.raspberrypi.org/downloads/noobs/](https://www.raspberrypi.org/downloads/noobs/)*
* Format SD card using [SD Card Formatter](https://www.sdcard.org/downloads/formatter_4/). Set "FORMAT SIZE ADJUSTMENT" option to "ON" in the "Options" menu to ensure that the entire SD card volume is formatted.
* Extract the downloaded NOOBS zip file in SD card and make sure the extracted file is not present in folder.
* Insert the SD card in Raspberry Pi, connect the Mouse, Keyboard and connect Power supply across it.
* Install Raspbian as Default OS.

Run 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
to run latest build.

You have successfully installed NOOBS in your Raspberry Pi!
