## Gst pipeline examples
#### testsrc all patterns
```
gst-launch-1.0 videomixer name=\"mix\" sink_0::xpos=0 sink_0::ypos=0 sink_1::xpos=200 sink_1::ypos=0 sink_2::xpos=400 sink_2::ypos=0 sink_3::xpos=600 sink_3::ypos=0 sink_4::xpos=800 sink_4::ypos=0 sink_5::xpos=0 sink_5::ypos=200 sink_6::xpos=200 sink_6::ypos=200 sink_7::xpos=400 sink_7::ypos=200 sink_8::xpos=600 sink_8::ypos=200 sink_9::xpos=800 sink_9::ypos=200 sink_10::xpos=0 sink_10::ypos=400 sink_11::xpos=200 sink_11::ypos=400 sink_12::xpos=400 sink_12::ypos=400 sink_13::xpos=600 sink_13::ypos=400 sink_14::xpos=800 sink_14::ypos=400 sink_15::xpos=0 sink_15::ypos=600 sink_16::xpos=200 sink_16::ypos=600 sink_17::xpos=400 sink_17::ypos=600 sink_18::xpos=600 sink_18::ypos=600 sink_19::xpos=800 sink_19::ypos=600 sink_20::xpos=0 sink_20::ypos=800 sink_21::xpos=200 sink_21::ypos=800 sink_22::xpos=400 sink_22::ypos=800 sink_23::xpos=600 sink_23::ypos=800 sink_24::xpos=800 sink_24::ypos=800 ! autovideosink videotestsrc pattern=0 ! video/x-raw,width=200,height=200 ! mix.sink_0 videotestsrc pattern=1 ! video/x-raw,width=200,height=200 ! mix.sink_1 videotestsrc pattern=2 ! video/x-raw,width=200,height=200 ! mix.sink_2 videotestsrc pattern=3 ! video/x-raw,width=200,height=200 ! mix.sink_3 videotestsrc pattern=4 ! video/x-raw,width=200,height=200 ! mix.sink_4 videotestsrc pattern=5 ! video/x-raw,width=200,height=200 ! mix.sink_5 videotestsrc pattern=6 ! video/x-raw,width=200,height=200 ! mix.sink_6 videotestsrc pattern=7 ! video/x-raw,width=200,height=200 ! mix.sink_7 videotestsrc pattern=8 ! video/x-raw,width=200,height=200 ! mix.sink_8 videotestsrc pattern=9 ! video/x-raw,width=200,height=200 ! mix.sink_9 videotestsrc pattern=10 ! video/x-raw,width=200,height=200 ! mix.sink_10 videotestsrc pattern=11 ! video/x-raw,width=200,height=200 ! mix.sink_11 videotestsrc pattern=12 ! video/x-raw,width=200,height=200 ! mix.sink_12 videotestsrc pattern=13 ! video/x-raw,width=200,height=200 ! mix.sink_13 videotestsrc pattern=14 ! video/x-raw,width=200,height=200 ! mix.sink_14 videotestsrc pattern=15 ! video/x-raw,width=200,height=200 ! mix.sink_15 videotestsrc pattern=16 ! video/x-raw,width=200,height=200 ! mix.sink_16 videotestsrc pattern=17 ! video/x-raw,width=200,height=200 ! mix.sink_17 videotestsrc pattern=18 ! video/x-raw,width=200,height=200 ! mix.sink_18 videotestsrc pattern=19 ! video/x-raw,width=200,height=200 ! mix.sink_19 videotestsrc pattern=20 ! video/x-raw,width=200,height=200 ! mix.sink_20 videotestsrc pattern=21 ! video/x-raw,width=200,height=200 ! mix.sink_21 videotestsrc pattern=22 ! video/x-raw,width=200,height=200 ! mix.sink_22 videotestsrc pattern=23 ! video/x-raw,width=200,height=200 ! mix.sink_23 videotestsrc pattern=24 ! video/x-raw,width=200,height=200 ! mix.sink_24
```
#### testsrc all patterns to udp
```
gst-launch-1.0 videomixer name=\"mix\" sink_0::xpos=0 sink_0::ypos=0 sink_1::xpos=200 sink_1::ypos=0 sink_2::xpos=400 sink_2::ypos=0 sink_3::xpos=600 sink_3::ypos=0 sink_4::xpos=800 sink_4::ypos=0 sink_5::xpos=0 sink_5::ypos=200 sink_6::xpos=200 sink_6::ypos=200 sink_7::xpos=400 sink_7::ypos=200 sink_8::xpos=600 sink_8::ypos=200 sink_9::xpos=800 sink_9::ypos=200 sink_10::xpos=0 sink_10::ypos=400 sink_11::xpos=200 sink_11::ypos=400 sink_12::xpos=400 sink_12::ypos=400 sink_13::xpos=600 sink_13::ypos=400 sink_14::xpos=800 sink_14::ypos=400 sink_15::xpos=0 sink_15::ypos=600 sink_16::xpos=200 sink_16::ypos=600 sink_17::xpos=400 sink_17::ypos=600 sink_18::xpos=600 sink_18::ypos=600 sink_19::xpos=800 sink_19::ypos=600 sink_20::xpos=0 sink_20::ypos=800 sink_21::xpos=200 sink_21::ypos=800 sink_22::xpos=400 sink_22::ypos=800 sink_23::xpos=600 sink_23::ypos=800 sink_24::xpos=800 sink_24::ypos=800 ! 'video/x-raw,format=I420,width=1920,height=1080,framerate=30/1' ! omxh264enc ! h264parse ! rtph264pay pt=96 ! udpsink port=5600 host=127.0.0.1 videotestsrc pattern=0 ! video/x-raw,width=200,height=200 ! mix.sink_0 videotestsrc pattern=1 ! video/x-raw,width=200,height=200 ! mix.sink_1 videotestsrc pattern=2 ! video/x-raw,width=200,height=200 ! mix.sink_2 videotestsrc pattern=3 ! video/x-raw,width=200,height=200 ! mix.sink_3 videotestsrc pattern=4 ! video/x-raw,width=200,height=200 ! mix.sink_4 videotestsrc pattern=5 ! video/x-raw,width=200,height=200 ! mix.sink_5 videotestsrc pattern=6 ! video/x-raw,width=200,height=200 ! mix.sink_6 videotestsrc pattern=7 ! video/x-raw,width=200,height=200 ! mix.sink_7 videotestsrc pattern=8 ! video/x-raw,width=200,height=200 ! mix.sink_8 videotestsrc pattern=9 ! video/x-raw,width=200,height=200 ! mix.sink_9 videotestsrc pattern=10 ! video/x-raw,width=200,height=200 ! mix.sink_10 videotestsrc pattern=11 ! video/x-raw,width=200,height=200 ! mix.sink_11 videotestsrc pattern=12 ! video/x-raw,width=200,height=200 ! mix.sink_12 videotestsrc pattern=13 ! video/x-raw,width=200,height=200 ! mix.sink_13 videotestsrc pattern=14 ! video/x-raw,width=200,height=200 ! mix.sink_14 videotestsrc pattern=15 ! video/x-raw,width=200,height=200 ! mix.sink_15 videotestsrc pattern=16 ! video/x-raw,width=200,height=200 ! mix.sink_16 videotestsrc pattern=17 ! video/x-raw,width=200,height=200 ! mix.sink_17 videotestsrc pattern=18 ! video/x-raw,width=200,height=200 ! mix.sink_18 videotestsrc pattern=19 ! video/x-raw,width=200,height=200 ! mix.sink_19 videotestsrc pattern=20 ! video/x-raw,width=200,height=200 ! mix.sink_20 videotestsrc pattern=21 ! video/x-raw,width=200,height=200 ! mix.sink_21 videotestsrc pattern=22 ! video/x-raw,width=200,height=200 ! mix.sink_22 videotestsrc pattern=23 ! video/x-raw,width=200,height=200 ! mix.sink_23 videotestsrc pattern=24 ! video/x-raw,width=200,height=200 ! mix.sink_24
```
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
