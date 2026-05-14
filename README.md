# libfranka: C++ library for Franka Robotics research robots

[![Build Status][travis-status]][travis]
[![codecov][codecov-status]][codecov]

With this library, you can control research versions of Franka Robotics robots. See the [Franka Control Interface (FCI) documentation][fci-docs] for more information about what `libfranka` can do and how to set it up. The [generated API documentation][api-docs] also gives an overview of its capabilities.

## Install

This library can be installed by following these steps from your colcon workspace root:

```bash
git clone --recurse-submodules git@github.com:unisa-acg/libfranka.git src/libfranka
cd src/libfranka
git submodule update --init --recursive
cd -
colcon build --cmake-args -DCMAKE_BUILD_TYPE=Release
```

If some compilation workings appear on `googletest`, you can safely ignore them.

## License

`libfranka` is licensed under the [Apache 2.0 license][apache-2.0].

[apache-2.0]: https://www.apache.org/licenses/LICENSE-2.0.html
[api-docs]: https://frankaemika.github.io/libfranka
[fci-docs]: https://frankaemika.github.io/docs
[travis-status]: https://travis-ci.org/frankaemika/libfranka.svg?branch=master
[travis]: https://travis-ci.org/frankaemika/libfranka
[codecov-status]: https://codecov.io/gh/frankaemika/libfranka/branch/master/graph/badge.svg
[codecov]: https://codecov.io/gh/frankaemika/libfranka
