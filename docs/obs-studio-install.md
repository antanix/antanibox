## OBS Studio

We install OBS Studio from source it's include plugins:
  - browser source
  - source record

### Installation procedure

Install needed packages
```
sudo apt-get install \
  build-essential cmake git \
  libmbedtls-dev libasound2-dev libavcodec-dev \
  libavdevice-dev libavfilter-dev libavformat-dev \
  libavutil-dev libcurl4-openssl-dev libfdk-aac-dev \
  libfontconfig-dev libfreetype6-dev libglvnd-dev \
  libjack-jackd2-dev libjansson-dev libluajit-5.1-dev \
  libpulse-dev libqt5x11extras5-dev libspeexdsp-dev \
  libswresample-dev libswscale-dev libudev-dev \
  libv4l-dev libvlc-dev libwayland-dev \
  libx11-dev libx264-dev libxcb-shm0-dev \
  libxcb-xinerama0-dev libxcomposite-dev libxinerama-dev \
  pkg-config python3-dev qtbase5-dev \
  qtbase5-private-dev libqt5svg5-dev swig \
  libxcb-randr0-dev libxcb-xfixes0-dev libx11-xcb-dev \
  libxcb1-dev libxss-dev qtwayland5 \
  libgles2-mesa libgles2-mesa-dev libnss3-dev
```

Download CEF
```
wget https://cdn-fastly.obsproject.com/downloads/cef_binary_4280_linux64.tar.bz2
tar -xjf ./cef_binary_4280_linux64.tar.bz2
```

Download OBS Studio sources:
```
git clone --recursive https://github.com/antanix/obs-studio.git
```

Build setup:
```
cd obs-studio
mkdir build && cd build
cmake -DUNIX_STRUCTURE=1 -DENABLE_PIPEWIRE=OFF -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_BROWSER=ON -DCEF_ROOT_DIR="../../cef_binary_4280_linux64" ..
```

Build
```
make -j$(nproc)
```

Install
```
sudo make install
```
