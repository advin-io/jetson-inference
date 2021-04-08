<img src="https://github.com/advin-io/jetson-inference/raw/master/docs/images/inference-stream.png" width="100%">
# WyzeCam Inference

Wireless real-time inference using NVIDIA Jetson and WyzeCam v2 over RTSP.

## The Idea

It started with me looking for a cost effective to track my location in the house for automation. Also:

1) I hate wires.

2) I want to keep my data local.

3) I like to do things as cheaply as possible.

## The Hardware

I first heard of the <a href="https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-nano/product-development/#shop-all">Jetson Nano</a> in 2019 but couldn't find a cost-effective camera to add to my network until I found:
<a href="https://wyze.com/wyze-cam.html">the $24 Wyze Cam.<img src=https://github.com/advin-io/jetson-inference/raw/master/docs/images/wyzecam.png></a>

## The Setup

I prefer to Dockerize everything because although it makes it harder for me, it makes it easier for you (and future me).

* <a href="https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script">Install Docker the quick (unsafe) way!</a>   
* [Build jetson-inference image](docs/aux-docker.md) (don't forget to <a href="https://github.com/dusty-nv/jetson-containers#docker-default-runtime">configure the runtime!</a>). This takes about 20 minutes unfortunately, but you only have to do it once!
* <a href="https://wyzelabs.zendesk.com/hc/en-us/articles/360026245231-Wyze-Cam-RTSP">Flash your Wyze Cam v2 or Pan (v3 not compatible...yet) with the RTSP firmware</a> (not compatible with microSDXC, I made this mistake for you)

## Running it

By now you should have an RTSP URL in the app (looks like rtsp://<Username>:<Password>@<IP>/live), so getting started is as easy as:

```bash
user@host:~$ cd jetson-inference # move to repo directory
user@host:~$ docker/run.sh # run the container
user@container:~$ detectnet rtsp://<Username>:<Password>@<IP>/live # May take a bit to build the first TensorRT enginer
```

## More to come! ...robots?
