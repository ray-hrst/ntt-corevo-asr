# NTT Corevo Speech Recognition
This is an unofficial git repo for a Docker image of NTT's Corevo Speech Recognition SDK build environment.

To build the image:
```
$ cd ntt/
$ docker build -t ntt-corevo-asr .
```

The Dockerfile requires the `AsrTestDriver.sh` file, which also has the user's API credentials. This file is not included here for security reasons. Go to [NTT Corevo API Portal](https://corevo-api-portal.xfarm.jp/en/) to get your credentials and download the Speech Recognition SDK. The `AsrTestDriver.sh` file is located in `corevo_ASR_SDK_for_Linux_v1.0.1.0/testDriver/bin/`.

Run the default example:
```
$ docker run ntt-corevo-asr
```
This runs the `AsrTestDriver.sh` file, which by default transcribes the `./pcm/ja_short.pcm` file that is already in the container.

Run a custom voice sample:
```
$ docker run -v /host/path:/container/path ntt-corevo-asr -f /container/path/<filename>.wav
```

where
* `/host/path` is the path to the folder containing the `.wav` file on the host machine
* `/container/path` is a unique path in the container that will be used to mount the `/host/path`

For example:
```
$ docker run -v /home/rayhrst/data/:/home/data/ ntt-corevo-asr -f /home/data/input.wav
```
