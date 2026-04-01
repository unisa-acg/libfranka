# libfranka: C++ library for Franka Robotics research robots

[![Build Status][travis-status]][travis]
[![codecov][codecov-status]][codecov]

With this library, you can control research versions of Franka Robotics robots. See the [Franka Control Interface (FCI) documentation][fci-docs] for more information about what `libfranka` can do and how to set it up. The [generated API documentation][api-docs] also gives an overview of its capabilities.

## Install

This library can be installed by following these steps:

```bash
git clone --recurse-submodules https://github.com/unisa-acg/libfranka
cd libfranka
git submodule update --init --recursive
mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local ..
cmake --build . -- -j$(nproc)
cpack -G DEB
sudo dpkg -i libfranka*.deb
```

### Verify the installation

The output of this procedure should be the following:

1. Check library file:

    ```bash
    ls -l /usr/lib/libfranka.so
    ```

    Expected output:

    ```text
    /usr/lib/libfranka.so -> libfranka.so.0.9
    ```

1. Check header files:

    ```bash
    ls /usr/include/franka/
    ```

    Expected output:

    ```text
    active_control_base.h  active_motion_generator.h  control_tools.h  duration.h  exception.h  gripper_state.h  lowpass_filter.h  rate_limiting.h  robot_state.h     vacuum_gripper_state.h
    active_control.h       active_torque_control.h    control_types.h  errors.h    gripper.h    log.h            model.h           robot.h          vacuum_gripper.h
    ```

1. Check installed package version:

    1. Check with `dpkg`:

        ```bash
        dpkg -l | grep libfranka
        ```
  
        Expected output:
  
        ```text
        ii  libfranka                                            0.9.3-1                                    amd64        libfranka built using CMake
        ```

      1. Check with `apt`:

         ```bash
         apt list -i | grep libfranka
         ```

         Expected output:

         ```text
         libfranka/now 0.9.3-1 amd64 [installed,local]
         ```

## License

`libfranka` is licensed under the [Apache 2.0 license][apache-2.0].

[apache-2.0]: https://www.apache.org/licenses/LICENSE-2.0.html
[api-docs]: https://frankaemika.github.io/libfranka
[fci-docs]: https://frankaemika.github.io/docs
[travis-status]: https://travis-ci.org/frankaemika/libfranka.svg?branch=master
[travis]: https://travis-ci.org/frankaemika/libfranka
[codecov-status]: https://codecov.io/gh/frankaemika/libfranka/branch/master/graph/badge.svg
[codecov]: https://codecov.io/gh/frankaemika/libfranka
