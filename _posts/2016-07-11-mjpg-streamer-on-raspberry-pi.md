---
layout: post
title: Installing MJPG Streamer on Raspberry Pi
tags: [Raspberry Pi, MJPG Streamer, Video]
category: Raspberry Pi Tutorials
thumbnail : thumbs/mjpg-streamer-on-raspberry-pi.png
excerpt: You want to stream video through Raspberry Pi
---
<img width="600"   alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" src="/thumbs/{{post.thumbnail}}">
>You want to stream video through Raspberry Pi

* Do not remove this line (it will not be displayed)
{:toc}

## A. Essentials

  Requirements:

    - Raspberry Pi
    - Raspberry Pi Camera Module


## B. Connect the Camera Module


![Raspberry Pi Camera Port]({{site.url}}/images/raspb-camera-connection.png "Raspberry Pi Camera Port"){: .center-image }*Camera connection from both sides*
  - Locate the camera port and connect the camera as shown.
  - Open the `Raspberry Pi Configuration` Tool from `Preferences` on the main menu

![Raspberry Pi Camera Enable]({{site.url}}/images/raspi-camera-config.png "Raspberry Pi Camera Enable"){: .center-image }

  - Enable the `Camera` from `Interfaces` tab if Disabled and Reboot the Pi.


## C. Installing MJPG Streamer


  Install dev version of libjpeg:


```
sudo apt-get install libjpeg62-turbo-dev
```


  Install make:

```
 sudo apt-get install cmake
```


  Download mjpg-streamer with raspicam plugin:


```
git clone https://github.com/jacksonliam/mjpg-streamer.git ~/mjpg-streamer
```


  Change directory:


```
 cd ~/mjpg-streamer/mjpg-streamer-experimental
 ```


  Compile:


 ```
 make clean all
 ```

  Replace old jpg-streamer:


 ```
 sudo rm -rf /opt/mjpg-streamer

sudo mv ~/mjpg-streamer/mjpg-streamer-experimental /opt/mjpg-streamer

sudo rm -rf ~/mjpg-streamer
 ```


## D. Start Streaming


  To Begin streaming type:


```
 LD_LIBRARY_PATH=/opt/mjpg-streamer/ /opt/mjpg-streamer/mjpg_streamer -i "input_raspicam.so -fps 15 -q 50 -x 640 -y 480" -o "output_http.so -p 9000 -w /opt/mjpg-streamer/www"
```


  You will see something like this

```
MJPG Streamer Version.: 2.0

i: fps.............: 15

i: resolution........: 640 x 480

i: camera parameters..............:

Sharpness 0, Contrast 0, Brightness 50, Saturation 0,

ISO 400, Video Stabilisation No, Exposure compensation 0

Exposure Mode 'auto', AWB Mode 'auto',

Image Effect 'none', Metering Mode 'average',

Colour Effect Enabled No with U = 128, V = 128

Rotation 0, hflip No, flip No

www-folder-path...: /opt/mjpg-streamer/www/

HTTP TCP port.....: 9000

username:password.: disabled

commands..........: enabled

Starting Camera

Encoder Buffer Size 81920
```
  Now type the following url in your browser

  To find IP address type

```
sudo ifconfig
```

  It will be something like this `192.168.43.100`
```
IpAddress:9000/stream.html
```

## E. Stop Streaming


  To stop streaming type:


```
kill -9 'pidof mjpg_streamer'
```
