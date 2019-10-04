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

By default, Docker may only be run by root users so that the output video is created with root permissions.
This behavior may be adjusted by using an account that is member of the `docker` group.

Example for adding user `alice` to group `docker`:
```$ sudo addgroup alice docker```

The converter may then be started by user `alice`; the output file will be created with permissions for user `alice`.

## Examples
Convert a video to a small MP4 with stereo audio in german for use on a mobile device:
```$ ./start /media/input.mkv /tmp/output.mp4```

Use italian language:
```$ AUDIO_LANGUAGE=ita ./start /media/input.mkv /tmp/output.mkv```

## Environment variables
The following list shows environment variables that may be used to adjust the format of the output video, together with their defaults.
- `VIDEO_BITRATE=1280k`
- `VIDEO_CODEC=h264_vaapi`
- `VIDEO_WIDTH=720`
- `AUDIO_BITRATE=128k`
- `AUDIO_CODEC=aac`
- `AUDIO_CHANNELS=2`
- `AUDIO_LANGUAGE=deu`
- `VAAPI_DEVICE=/dev/dri/renderD128`
