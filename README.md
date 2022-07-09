# drm-510-kmod-FreeBSD-13 [![Build Status](https://api.cirrus-ci.com/github/helloSystem/drm-510-kmod-FreeBSD-13.svg)](https://cirrus-ci.com/github/helloSystem/drm-510-kmod-FreeBSD-13)

Upstream: https://github.com/freebsd/drm-kmod/

## Rationale

As of 2022Q2, for Intel TigerLake-LP GT2 [Iris Xe Graphics] `8086:9a49:f111:0001` GPUs to get recognized and working properly, we need `graphics/drm-510-kmod` (at some time in the future, `graphics/drm-kmod` should do the right thing).

However, as of 2022Q2, there is no package of `graphics/drm-kmod` for FreeBSD 13 yet because `graphics/drm-510-kmod` requires at least FreeBSD 13.1 but FreeBSD 13.0 is still supported, and packages will only start to be built against FreeBSD 13.1 once FreeBSD 13.0 is no longer supported.

This is why we need to build `graphics/drm-510-kmod` ourselves if we don't want to wait until FreeBSD 13.0 is no longer supported and `graphics/drm-510-kmod` will land in quarterly packages (which helloSystem is using).

## Approach

We build just the one package we are interested in using Cirrus CI in under 3 minutes by downloading only the sections of the FreeBSD Ports tree that we really need using git. Then we use the resulting pkg [here](https://github.com/helloSystem/ISO/blob/c80fd5ab71394507fd363218e8ad37bfef527357/settings/packages.common-13#L21).

## Issues

https://www.freshports.org/graphics/drm-devel-kmod says:

```
For now please use drm-510-kmod and if you have problems with it
please use drm-54-kmod and open a issue on https://github.com/freebsd/drm-kmod
```
