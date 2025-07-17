# ffmpeg-rtsp-capture
I have a camera that supports rtsp and I need to continuously capture the data, so here we go!

# Requirements
[ffmpeg](https://ffmpeg.org/), along with ffprobe

# Crons
Note: /mnt/usb14 is an external USB drive. ymmv

```
# Streaming local cameras - 10m segments
*/10 * * * * cd /mnt/usb14/Camera && ./rtsp-recorder 2>&1 >/dev/null
2 2 * * * cd /mnt/usb14/Camera && ./make-the-day 2>&1 >/dev/null
```

## rtsp-recorder
bread-and-butter. every 10 minutes records an original stream from an authenticated rtsp source.

## make-the-day
combined all the videos into one long one. leaves the rest for later pruning
