# Opendevices IoT Workshop

For this workshop we need :

  - Raspberry PI  with Raspbian system.
  - Usb camera.
  - vlc software.
  - Computer and internet browser.
  - Network connection.


In this workshop we are going to use a  raspberry pi and vlc software to record video
from a usb camera connected to the rpi and output the stream over  network using http
protocol , so you can read it form your computer using a internet browser.



## 1. Installing vlc

Open a terminal and type the following command to install vlc

```bash
$ sudo apt-get -y install vlc
```


## 2. Capture video streaming


  - Launch vlc
  - Click on media then Open Capture Device.

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/CaptureDevice.png)

  - Click on the arrow button near Play button and choose stream.

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/SelectStream.png)

  - Click next

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/StreamSource.png)

  - For new destinatioin choose HTTP.

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/SelectHTTP.png)

  - Then click on Add

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/SelectDestination.png)

  - Click on profile to choose a video format then next.

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/VideoTranscode.png)

  - Click stream

![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/StreamOutput.png)


## 3. Read the video streaming from your computer.

  - Open internet browser.
  - Type the IP address of raspberry pi and the  port number chosen in vlc config like that **http://192.168.1.102:8080**.

 ![vlc open device](https://github.com/opendevices/iot.apps/blob/master/workshop/)

 - Say hello to the camera ;)


## 4. Raspbian system without graphical interface.

If you have installed rapsbian without GUI you can connect to your system using ssh
and launch vlc via command line.

  - Connect to your raspbberry.

```bash
$ ssh -l pi raspberrypi.local

```

  - Launch vlc

```bash
$ vlc -vvv v4l2:///dev/video0 --sout '#transcode{vcodec=VP80,vb=2000,acodec=vorb,ab=128,channels=2,samplerate=44100}:http{mux=webm,dst=:8080/}' --no-sout-all --sout-keep
```
