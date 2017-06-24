---
layout: post
title: Installing MJPG Streamer on Raspberry Pi
tags: [Raspberry Pi, MJPG Streamer, Video]
category: Raspberry Pi Tutorials
thumbnail: /thumbs/mjpg-streamer-on-raspberry-pi.png
description: Streaming video output on webserver or media player through camera connected on Raspberry Pi can be used for many applications. You can stream video from Raspberry Pi Camera to Web Browsers, even on Android, IOS and Windows!
---
<div class="row">
<div class="col-md-10">
<div class="intro">
<img src="{{ page.thumbnail }}" alt="{{page.title}}">
<i class="fa fa-quote-left fa-2x fa-pull-left fa-border"></i>
<p>{{page.description}}</p>
</div>
</div>
</div>

Motion JPG is a video compression format in which each video frame or video sequence is compressed separately as a JPEG image. MJPG-streamer takes JPGs from compatible cameras or other input plugins and streams them as M-JPEG via HTTP to web browsers and other media players.

* Do not remove this line (it will not be displayed)
{:toc}

## A. Essentials

Requirements:

  - Raspberry Pi
  - Raspberry Pi Camera Module


## B. Connect the Camera Module


![Raspberry Pi Camera Port](/images/raspb-camera-connection.png "Raspberry Pi Camera Port"){: .center-image }*Camera connection from both sides*
  - Locate the camera port and connect the camera as shown.
  - Open the `Raspberry Pi Configuration` Tool from `Preferences` on the main menu

![Raspberry Pi Camera Enable](/images/raspi-camera-config.png "Raspberry Pi Camera Enable"){: .center-image }

  - Enable the `Camera` from `Interfaces` tab if Disabled and Reboot the Pi.


## C. Installing Dependencies

  Install dev version of libjpeg:

```
sudo apt-get install libjpeg62-turbo-dev
```

  Install make:

```
 sudo apt-get install cmake
```

## D. Installing MJPG Streamer

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


## E. Start Streaming


  To Begin streaming type:


```
 LD_LIBRARY_PATH=/opt/mjpg-streamer/ /opt/mjpg-streamer/mjpg_streamer -i "input_raspicam.so -fps 15 -q 50 -x 640 -y 480" -o "output_http.so -p 9000 -w /opt/mjpg-streamer/www"
 ```

You can change the above parameters

| Parameter 	|      Point      	|                Details               	|
|:---------:	|:---------------:	|:------------------------------------:	|
|     -i    	|      input      	|           input parameters           	|
|     -o    	|      output     	|           output parameters          	|
|    -fps   	|    framerate    	| video framerate, default 5 frame/sec 	|
|     -q    	|     quality     	|  set JPEG quality 0-100, default 85  	|
|     -x    	|   width/x-axis  	|  width of frame capture, default 640 	|
|     -y    	|  height/y-axis  	| height of frame capture, default 480 	|
|     -p    	|    HTTP port    	|     TCP port for this HTTP server    	|
|     -w    	| web page folder 	|     folder that contains webpages    	|
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
  Now type the this url in your browser `http://localhost:9000/stream.html` to view the streamed output locally or type the IP address of Raspberry Pi with port like `http://<IP-address>:9000/stream.html` to watch from another computer/device in your network.

  To find IP address enter:

```
sudo ifconfig
```

  It will be something like this `192.168.43.100`

## F. Stop Streaming

  To stop streaming type:
  
```
kill -9 'pidof mjpg_streamer'
```
