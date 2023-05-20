## Gst pipeline examples
#### libcamerasrc to autovideosink
```
gst-launch-1.0 libcamerasrc name=src src.src ! queue ! videoconvert ! autovideosink src.src_0 ! queue ! videoconvert ! autovideosink
```
#### udpsrc to fpsdisplaysink preview
```
gst-launch-1.0 -e udpsrc port=5600 caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96" ! rtph264depay ! decodebin ! videoconvert ! fpsdisplaysink sync=false
```
#### ximagesrc to filesink
```
gst-launch-1.0 ximagesrc ! video/x-raw,framerate=30/1 ! videoconvert ! x264enc bitrate=10000 speed-preset=veryfast tune=zerolatency ! matroskamux ! filesink location=$DIRNAME/$next_file    
```

#### lib-camera to gst
```
libcamera-vid -t 0 -k -n --inline --framerate 30 --mode 2312:1736 --width 1280 --height 720 --lens-position 6.5 --autofocus-mode manual -o - | \
gst-launch-1.0 fdsrc fd=0  name=src src.src ! h264parse ! avdec_h264 ! videoconvert ! autovideosink
```
#### ximagesrc to udpsink
```
gst-launch-1.0 ximagesrc ! videoscale ! video/x-raw,width=320,height=240,framerate=30/1 ! videoconvert ! x264enc bitrate=10000 speed-preset=superfast tune=zerolatency ! rtph264pay name=pay0 pt=96 ! udpsink host=192.168.0.1 port=5600 sync=false
```
#### lib-camera to multiudpsink. test
```
libcamera-vid -t 0 -k -n --inline --framerate 30 --mode 2312:1736 --width 1280 --height 720 --lens-position 6.5 --autofocus-mode manual -o - | \ 
gst-launch-1.0 fdsrc fd=0 ! h264parse ! rtph264pay ! multiudpsink clients=192.168.0.1:5600,127.0.0.1:5600 buffer-size=10485760
```
