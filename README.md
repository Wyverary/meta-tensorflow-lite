# TensorFlow Lite Python image classification demo

## Reference

- [TensorFlow Lite Python image classification demo - tensorflow/tensorflow](https://github.com/tensorflow/tensorflow/blob/v2.19.0/tensorflow/lite/examples/python/README.md)

## How to
Build sample on Raspberry Pi 4 AArch64 (core-image-weston).

### Clone repositories and oe-init-build-env.
```
git clone git://git.yoctoproject.org/poky.git
git clone git://git.yoctoproject.org/meta-raspberrypi
git clone git://git.openembedded.org/meta-openembedded
git clone https://github.com/NobuoTsukamoto/meta-tensorflow-lite.git
source poky/oe-init-build-env build
```

### Add layer
```
bitbake-layers add-layer ../meta-openembedded/meta-oe/
bitbake-layers add-layer ../meta-openembedded/meta-python/
bitbake-layers add-layer ../meta-openembedded/meta-networking/
bitbake-layers add-layer ../meta-openembedded/meta-multimedia/
bitbake-layers add-layer ../meta-raspberrypi/
bitbake-layers add-layer ../meta-tensorflow-lite/
```

### Create conf/auto.conf file and write config
Add `python3-tensorflow-lite`, `python3-tensorflow-lite-example` and `python3-pillow` recipes to `conf/auto.conf` file.
```
IMAGE_INSTALL:append = " python3-tensorflow-lite-example"
```

### Bitbake
```
MACHINE=raspberrypi4-64 bitbake core-image-weston
```

