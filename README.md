# libfranka: C++ library for Franka Robotics research robots

[![Build Status][travis-status]][travis]
[![codecov][codecov-status]][codecov]

With this library, you can control research versions of Franka Robotics robots. See the [Franka Control Interface (FCI) documentation][fci-docs] for more information about what `libfranka` can do and how to set it up. The [generated API documentation][api-docs] also gives an overview of its capabilities.

## Dependencies

The dependency of this library can be resolved via `rosdep`:

1. Move to your colcon workspace root folder, e.g.

  ```bash
  cd ~/ros2_ws/  # Change folder based on your system
  ```

2. Clone this repository

  ```bash
  git clone --recurse-submodules git@github.com:unisa-acg/libfranka.git src/libfranka
  cd src/libfranka/
  git submodule update --init --recursive
  cd -
  ```

3. Install dependencies (you need to be a superuser to do so)

  ```bash
  rosdep install --from-paths src -y -i
  ```

## Install

This library can be installed via `colcon` from your colcon workspace root:

```bash
colcon build --packages-up-to libfranka --cmake-args -DCMAKE_BUILD_TYPE=Release
```

If some compilation workings appear on `googletest`, you can safely ignore them.

## Tracing FCI loop timing (LTTng-UST)

The `generate_joint_position_motion_external_control_loop` example is instrumented with a `franka_timing` LTTng-UST tracepoint provider, so FCI read/write timings can be captured and compared against traces from the `franka_hardware` plugins in `franka_ros2`, which use the identical provider definition.
It needs `liblttng-ust-dev` (2.13.x) and is built by default; pass `-DWITH_LTTNG=OFF` to disable it.

Capture workflow:

```bash
lttng create franka-timing
lttng enable-event -u 'franka_timing:*'
lttng start
./build/libfranka/examples/generate_joint_position_motion_external_control_loop <robot-hostname>
lttng stop
lttng destroy
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
