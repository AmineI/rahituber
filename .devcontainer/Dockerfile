FROM mcr.microsoft.com/devcontainers/cpp:3-debian13

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        freeglut3-dev \
        libasound2-dev \
        libbrotli-dev \
        libbz2-dev \
        libxcursor-dev \
        libflac-dev \
        libjack-dev \
        libogg-dev \
        libopenal-dev \
        libpng-dev \
        libudev-dev \
        libvorbis-dev \
        libx11-dev \
        libxrandr-dev \
        uuid-dev \
        zlib1g-dev \
    && rm -rf /var/lib/apt/lists/*
