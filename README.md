# VAAPI video converter
A Docker-based video converter that uses VAAPI-compatible hardware for transcoding

## Key features
- Transcode a video
- Keep only the main video and a single audio track
- Use hardware-acceleration to unburden the CPU
- Use docker to keep the system clean of dependent packages

## Pre-requisites
- A linux system with `docker-compose`

On debian-based systems, `docker-compose` may be installed by calling

```$ sudo apt install docker-compose```

## Examples
Convert a video to a small MP4 with stereo audio in german for use on a mobile device:

```$ ./start /media/input.mkv /tmp/output.mp4```

Use italian language; if not available, use english as fallback:

```$ AUDIO_LANGUAGES=ita,eng ./start /media/input.mkv /tmp/output.mkv```

Create output video with permissions for user with user id and group id 1000:

```$ PUID=1000 PGID=1000 ./start /media/input.mkv /tmp/output.mp4```

## Environment variables
The following list shows environment variables that may be used to adjust the format of the output video, together with their defaults.
- `VIDEO_BITRATE=1280k`
- `VIDEO_CODEC=h264_vaapi`
- `VIDEO_WIDTH=720`
- `AUDIO_BITRATE=128k`
- `AUDIO_CODEC=aac`
- `AUDIO_CHANNELS=2`
- `AUDIO_LANGUAGES=deu,ger,eng`
- `VAAPI_DEVICE=/dev/dri/renderD128`
- `PUID`=_uid of current user_
- `GUID`=_group of current user_
