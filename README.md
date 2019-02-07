# CMake builder images

|              |   |   |    |
|:--           |:--|:--|:---|
| Debian       | [![Docker Stars](https://img.shields.io/docker/stars/starwarsfan/cmake-builder-debian.svg)](https://hub.docker.com/r/starwarsfan/cmake-builder-debian/) | [![Docker Pulls](https://img.shields.io/docker/pulls/starwarsfan/cmake-builder-debian.svg)](https://hub.docker.com/r/starwarsfan/cmake-builder-debian/) | [![ImageLayers](https://images.microbadger.com/badges/image/starwarsfan/cmake-builder-debian.svg)](https://microbadger.com/#/images/starwarsfan/cmake-builder-debian) |
| Fedora       | [![Docker Stars](https://img.shields.io/docker/stars/starwarsfan/cmake-builder-fedora.svg)](https://hub.docker.com/r/starwarsfan/cmake-builder-fedora/) | [![Docker Pulls](https://img.shields.io/docker/pulls/starwarsfan/cmake-builder-fedora.svg)](https://hub.docker.com/r/starwarsfan/cmake-builder-fedora/) | [![ImageLayers](https://images.microbadger.com/badges/image/starwarsfan/cmake-builder-fedora.svg)](https://microbadger.com/#/images/starwarsfan/cmake-builder-fedora) |

## Builder images with preinstalled CMake and C++ toolchain

This repository contains Dockerfiles to create builder images with
a complete preinstalled CMake and C++ toolchain.

## How it is build
```
docker build \
    -f <distribution>/Dockerfile \
    -t starwarsfan/cmake-builder-<distribution>:latest \
    .
```
