```batch
ffmpeg -list_devices true -f dshow -i dummy

[dshow @ 02457a60] DirectShow video devices
[dshow @ 02457a60]  "Blackmagic WDM Capture"
[dshow @ 02457a60]  "Decklink Video Capture"
[dshow @ 02457a60] DirectShow audio devices
[dshow @ 02457a60]  "Decklink Audio Capture"
```

```batch
ffmpeg -list_options true -f dshow -i video="Decklink Video Capture"

[dshow @ 03c2ea20] DirectShow video device options
[dshow @ 03c2ea20]  Pin "Capture"
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=720x486 fps=29.97 max s=720x486 fps=29.97
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=720x486 fps=23.976 max s=720x486 fps=23.976
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=720x576 fps=25 max s=720x576 fps=25
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=720x486 fps=59.9402 max s=720x486 fps=59.9402
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=720x576 fps=50 max s=720x576 fps=50
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1920x1080 fps=23.976 max s=1920x1080 fps=23.976
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1920x1080 fps=24 max s=1920x1080 fps=24
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1920x1080 fps=25 max s=1920x1080 fps=25
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1920x1080 fps=29.97 max s=1920x1080 fps=29.97
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1920x1080 fps=30 max s=1920x1080 fps=30
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1280x720 fps=50 max s=1280x720fps=50
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1280x720 fps=59.9402 max s=1280x720 fps=59.9402
[dshow @ 03c2ea20]   pixel_format=uyvy422  min s=1280x720 fps=60.0002 max s=1280x720 fps=60.0002
```

```batch
ffmpeg -list_options true -f dshow -i audio="Decklink Audio Capture"

[dshow @ 047fea20] DirectShow audio device options
[dshow @ 047fea20]  Pin "Capture"
[dshow @ 047fea20]   min ch=1 bits=16 rate= 48000 max ch=1 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=2 bits=16 rate= 48000 max ch=2 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=4 bits=16 rate= 48000 max ch=4 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=6 bits=16 rate= 48000 max ch=6 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=8 bits=16 rate= 48000 max ch=8 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=10 bits=16 rate= 48000 max ch=10 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=12 bits=16 rate= 48000 max ch=12 bits=16 rate= 48000
[dshow @ 047fea20]   min ch=16 bits=16 rate= 48000 max ch=16 bits=16 rate= 48000
```

```batch
ffmpeg -f dshow -video_size 1280x720 -rtbufsize 702000k -framerate 60 -i video="Decklink Video Capture":audio="Decklink Audio Capture" -r 30 -threads 4 -vcodec libx264 -crf 0 -preset ultrafast -f mpegts "udp://239.255.12.42:6666"
ffmpeg -y -threads 4 -i udp://239.255.12.42:6666 -map 0 -acodec copy -vcodec copy output.mkv
```
