## Gst pipeline examples
#### v4l2src preview
```
gst-launch-1.0   v4l2src !   autovideoconvert !  videoscale !  video/x-raw,width=1280 ! ximagesink
```
#### libcamerasrc to autovideosink
```
gst-launch-1.0 libcamerasrc name=src src.src ! queue ! videoconvert ! autovideosink src.src_0 ! queue ! videoconvert ! autovideosink
```
#### udpsrc to fpsdisplaysink preview
```
gst-launch-1.0 -e udpsrc port=5600 caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96" ! rtph264depay ! decodebin ! videoconvert ! fpsdisplaysink sync=false
```
#### udpsrc to filesink mp4
```
gst-launch-1.0 -e udpsrc port=5600 caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96" ! rtph264depay ! video/x-h264 ! queue ! h264parse ! queue ! mp4mux ! filesink location=/media/pi/CA62-CAC1/rpivideo/video.mp4
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
### UDP
#### v4l2src to multiudpsink
```
gst-launch-1.0 v4l2src device=/dev/video0  ! autovideoconvert ! x264enc tune=zerolatency ! rtph264pay config-interval=1 pt=96 mtu=1400 aggregate-mode=zero-latency ! multiudpsink clients=192.168.144.20:5600,127.0.0.1:5600 buffer-size=10485760
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

#### ht-301 to wfb-ng
```
v4l2src device=/dev/video1 ! video/x-raw ! videocrop top=0 left=0 right=0 bottom=4 ! videoconvert ! x264enc  tune=zerolatency ! h264parse config-interval=3 ! rtph264pay mtu=1400 ! udpsink host=127.0.0.1 port=5602 sync=false
```


## GSTD
#### videocrop aka ZOOM
```
pipeline_create testpipe videotestsrc ! videocrop top=42 left=1 right=4 bottom=0 name=crp ! ximagesink
pipeline_play testpipe
element_set testpipe crp top 100
```


## DUAL CAMERA test (ximagesrc)
#### This is my stereo camera pipeline:
```
gst-launch-1.0 videomixer name=m sink_1::xpos=320 ! autovideoconvert ! ximagesink sync=false v4l2src !   autovideoconvert !  videoscale !  video/x-raw,width=320 ! m. ximagesrc startx=1920 !   autovideoconvert !  videoscale !  video/x-raw,width=1280 ! m.
```
