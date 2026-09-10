# RahiTuber

For info, please see the itch.io page: https://rahisaurus.itch.io/rahituber

# Building from source 

## Submodules

This project resolves many dependencies via submodule. When cloning you should use `git clone --recurse-submodules`.
Otherwise use `git submodule update --init`, as without this the project will not build correctly.



The following dependencies are included as submodules:
  - SFML 2.6.1
  - imgui
  - imgui-sfml (Included in-tree with my modifications)
  - portaudio
  - mongoose
  - tinyxml2
  - Spout2 (Only used on Win32)

## Package dependencies
You can use the provided [devcontainer](https://code.visualstudio.com/docs/devcontainers/tutorial) to start from an environment preconfigured with the correct dependencies

Mandatory Linux dependencies(apt packages included in parentheses):
  - LibX11 (libx11-dev)
  - libXrandr (libxrandr-dev)
  - libXcursor (libxcursor-dev)
  - libuuid (uuid-dev)
  - OpenGL (freeglut3-dev)
  - libudev (libudev-dev)
  - OpenAL (libopenal-dev)
  - libogg (libogg-dev)
  - libvorbis (libvorbis-dev)
  - libflac (libflac-dev)


Optional Linux dependencies (functionality may not work without these):
  - libpng (libpng-dev)
  - zlib (zlib1g-dev)
  - libbz2 (libbz2-dev)
  - alsa-lib (libasound2-dev)
  - libjack (libjack-dev)
  - libbrotli (libbrotli-dev)
 

## Building debug executable

To build create a directory in the project root to build from (`build` is the convention)
and use CMake to generate the project files.


On Linux environments, you can build a Linux executable with the following command
```bash
cmake -S . -B build \
  -DCMAKE_POLICY_VERSION_MINIMUM=3.5 \
  -DOpenGL_GL_PREFERENCE="GLVND" \
  -DCMAKE_BUILD_TYPE="Debug"
cmake --build build --parallel
```

### Cross-compiling for Windows on Linux

Install the 64-bit MinGW-w64 toolchain (`mingw-w64` on Debian and Ubuntu), then
configure a separate build directory with the included toolchain file:

```bash
cmake -S . -B build-windows \
  -DCMAKE_TOOLCHAIN_FILE="cmake/mingw-w64-x86_64.cmake" \
  -DCMAKE_POLICY_VERSION_MINIMUM=3.5 \
  -DCMAKE_BUILD_TYPE="Debug"
cmake --build build-windows --target RahiTuber --parallel
```

The executable and its resource directory are written to
`build-windows/RahiTuber/`. The MinGW runtime DLLs must be distributed beside
the executable when they are not already available on the target Windows
system.