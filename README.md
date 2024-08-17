# rust-paho-mqtt-example

Example project to demonstrate paho-mqtt library dependency failure with Yocto Scarthgap SDK with Rust language extension.

## Requirements

See [Yocto system requirements](https://docs.yoctoproject.org/ref-manual/system-requirements.html).

## Compile SDK with rust language support

```
Download Poky reference distribution for Yocto Scarthgap:
$ git clone --branch scarthgap git://git.yoctoproject.org/poky

Initialize build environment:
$ cd poky
poky$ source oe-init-build-env

Enable SDK rust langage support in local.conf:
poky/build$ echo 'SDK_TOOLCHAIN_LANGS += "rust"' >> conf/local.conf

Populate SDK:
poky/build$ bitbake core-image-minimal -c populate_sdk -k

Install SDK:
poky/build$ tmp/deploy/sdk/poky-glibc-x86_64-core-image-minimal-core2-64-qemux86-64-toolchain-5.0.3.sh
```

## Build Project with SDK

```
Download this project:
$ git clone https://github.com/aabelix/rust-paho-mqtt-example

Initialize SDK environment:
poky/build$ source y/environment-setup-core2-64-poky-linux

Compile project:
$ cd rust-paho-mqtt-example
rust-paho-mqtt-example$ cargo build
    Updating crates.io index
  Downloaded paho-mqtt v0.9.2
  Downloaded paho-mqtt-sys v0.5.0
  Downloaded 2 crates (4.2 MB) in 3.23s (largest was `paho-mqtt-sys` at 4.1 MB)
   Compiling futures-core v0.3.30
   Compiling paho-mqtt-sys v0.5.0
   Compiling thiserror v1.0.63
   Compiling futures-channel v0.3.30
   Compiling futures-util v0.3.30
error: failed to run custom build command for `paho-mqtt-sys v0.5.0`

Caused by:
  process didn't exit successfully: `/git/github.com/epcpower/rust-paho-mqtt-example/target/debug/build/paho-mqtt-sys-efca27fad3e6629d/build-script-build` (exit status: 101)
  --- stdout
  debug:Running the bundled build for Paho C
  cargo:rerun-if-changed=build.rs
  CMAKE_TOOLCHAIN_FILE_x86_64-poky-linux-gnu = None
  CMAKE_TOOLCHAIN_FILE_x86_64_poky_linux_gnu = None
  TARGET_CMAKE_TOOLCHAIN_FILE = None
  CMAKE_TOOLCHAIN_FILE = Some("/yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/share/cmake/OEToolchainConfig.cmake")
  CMAKE_GENERATOR_x86_64-poky-linux-gnu = None
  CMAKE_GENERATOR_x86_64_poky_linux_gnu = None
  TARGET_CMAKE_GENERATOR = None
  CMAKE_GENERATOR = None
  CMAKE_PREFIX_PATH_x86_64-poky-linux-gnu = None
  CMAKE_PREFIX_PATH_x86_64_poky_linux_gnu = None
  TARGET_CMAKE_PREFIX_PATH = None
  CMAKE_PREFIX_PATH = None
  CMAKE_x86_64-poky-linux-gnu = None
  CMAKE_x86_64_poky_linux_gnu = None
  TARGET_CMAKE = None
  CMAKE = None
  running: cd "/git/github.com/epcpower/rust-paho-mqtt-example/target/x86_64-poky-linux-gnu/debug/build/paho-mqtt-sys-4d8a668a6160be6a/out/build" && CMAKE_PREFIX_PATH="" "cmake" "/yocto/poky/build/y/sysroots/core2-64-poky-linux/home/cargo/registry/src/index.crates.io-6f17d22bba15001f/paho-mqtt-sys-0.5.0/paho.mqtt.c/" "-DPAHO_BUILD_SHARED=off" "-DPAHO_BUILD_STATIC=on" "-DPAHO_ENABLE_TESTING=off" "-DPAHO_HIGH_PERFORMANCE=on" "-DPAHO_WITH_SSL=off" "-DCMAKE_TOOLCHAIN_FILE=/yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/share/cmake/OEToolchainConfig.cmake" "-DCMAKE_INSTALL_PREFIX=/git/github.com/epcpower/rust-paho-mqtt-example/target/x86_64-poky-linux-gnu/debug/build/paho-mqtt-sys-4d8a668a6160be6a/out" "-DCMAKE_C_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64 -pipe -feliminate-unused-debug-types" "-DCMAKE_CXX_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64 -pipe -feliminate-unused-debug-types" "-DCMAKE_ASM_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64 -pipe -feliminate-unused-debug-types" "-DCMAKE_BUILD_TYPE=Debug"
  -- The C compiler identification is GNU 13.3.0
  -- Detecting C compiler ABI info
  -- Detecting C compiler ABI info - failed
  -- Check for working C compiler: /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/x86_64-poky-linux/x86_64-poky-linux-gcc
  -- Check for working C compiler: /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/x86_64-poky-linux/x86_64-poky-linux-gcc - broken
  -- Configuring incomplete, errors occurred!

  --- stderr
  /usr/bin/env: symbol lookup error: /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/../../lib/libc.so.6: undefined symbol: __tunable_is_initialized, version GLIBC_PRIVATE
  CMake Deprecation Warning at CMakeLists.txt:20 (CMAKE_MINIMUM_REQUIRED):
    Compatibility with CMake < 3.5 will be removed from a future version of
    CMake.

    Update the VERSION argument <min> value or use a ...<max> suffix to tell
    CMake that the project does not need compatibility with older versions.


  CMake Error at /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/share/cmake-3.28/Modules/CMakeTestCCompiler.cmake:67 (message):
    The C compiler

      "/yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/x86_64-poky-linux/x86_64-poky-linux-gcc"

    is not able to compile a simple test program.

    It fails with the following output:

      Change Dir: '/git/github.com/epcpower/rust-paho-mqtt-example/target/x86_64-poky-linux-gnu/debug/build/paho-mqtt-sys-4d8a668a6160be6a/out/build/CMakeFiles/CMakeScratch/TryCompile-46BqHw'
      
      Run Build Command(s): /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/cmake -E env VERBOSE=1 /usr/bin/gmake -f Makefile cmTC_e8340/fast
      /usr/bin/gmake: symbol lookup error: /yocto/poky/build/y/sysroots/x86_64-pokysdk-linux/usr/bin/../../lib/libc.so.6: undefined symbol: __tunable_is_initialized, version GLIBC_PRIVATE
      
      

    

    CMake will not be able to correctly generate this project.
  Call Stack (most recent call first):
    CMakeLists.txt:21 (PROJECT)


  thread 'main' panicked at /yocto/poky/build/y/sysroots/core2-64-poky-linux/home/cargo/registry/src/index.crates.io-6f17d22bba15001f/cmake-0.1.51/src/lib.rs:1100:5:

  command did not execute successfully, got: exit status: 1

  build script failed, must exit now
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
warning: build failed, waiting for other jobs to finish...
```
