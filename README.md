![GitHub Workflow Status](https://img.shields.io/github/workflow/status/weilbyte/box/Docker%20build?style=flat-square) ![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/weilbyte/box?style=flat-square) ![Docker Pulls](https://img.shields.io/docker/pulls/weilbyte/box?style=flat-square)

![Box86 and Box64 logos](meta/box86box64.png)
# box
Comes with box86/box64 for emulating i386/amd64 workloads on armv7/arm64v8. Default entry point is `box86`/`box64` (depending on architecture), which can be found at `/usr/local/bin/box86`/ `/usr/local/bin/box64`. Image is rebuilt against box86/box64 master branch every 24 hours.

## Tags 
* `latest`, **`debian-11`** (*[arm64v8-debian-11/Dockerfile](arm64v8-debian-11/Dockerfile), [arm64v8-debian-11/Dockerfile](armv7-debian-11/Dockerfile)*)
* `armv7-debian-11` (*[arm64v8-debian-11/Dockerfile](armv7-debian-11/Dockerfile)*)
* `arm64v8-debian-11` (*[arm64v8-debian-11/Dockerfile](arm64v8-debian-11/Dockerfile)*)

> `arm64v8` variant comes with both `box86` and `box64`, built with dynamic recompilation enabled.
> `armv7` variant comes only with `box86`, built without dynamic recompilation.

## Usage

### Mount and run amd64 binary 
```sh
$ sudo docker run -it --rm -e BOX64_LOG=0 -v $(pwd):/binary weilbyte/box:debian-11 /binary/hello
Hello, world! This binary is compiled for amd64.
```
### Use as base Dockerfile image
```dockerfile
FROM weilbyte/box:debian-11

RUN /usr/local/bin/box64 --version
```

## Configuration
You can pass supported environment variables (as shown in the first example above). 
They can be found [here, for box86](https://github.com/ptitSeb/box86/blob/master/docs/USAGE.md) and [here, for box64](https://github.com/ptitSeb/box64/blob/master/docs/USAGE.md).

## Notable locations
* `/usr/local/bin/box86` box86 binary
* `/usr/local/bin/box64` box64 binary

## License
This repository is licensed under MIT.

box86 can be found [here](https://github.com/ptitSeb/box86) 
box64 can be found [here](https://github.com/ptitSeb/box64).
