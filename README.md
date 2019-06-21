# Launch Synergy Client headlessly
Somehow Synergy GUI doesn't play well with `Pop!_OS` (based on Ubuntu 18.04), but both Synergy Server and Client can run headlessly.

Create following shell script, add execution permission and add to startup application.
```
##!/bin/bash
SYNERGY_SVR_ADDR=YOUR_SERVER_ADDRESS
synergyc --daemon --debug INFO $SYNERGY_SVR_ADDR
```

# Use Barrier instead of Synergy for better stablity
1. Find release version from https://github.com/debauchee/barrier/releases and download binary for Windows and source code for Linux.

2. Follow https://github.com/debauchee/barrier/wiki/Building-on-Linux to build on Linux.
```
# For Ubuntu/Pop!_OS 18.04
sudo apt update && sudo apt upgrade
sudo apt install git cmake make xorg-dev g++ libcurl4-openssl-dev \
                 libavahi-compat-libdnssd-dev libssl-dev libx11-dev \
                 libqt4-dev qtbase5-dev
git clone git@github.com:debauchee/barrier.git
# this builds from master,
# you can get release tarballs instead
# if you want to build from a specific tag/release
cd barrier
./clean_build.sh
cd build
sudo make install  # installs to /usr/local/ 
```

3. Install extension to enable legacy system tray https://pop.system76.com/docs/status-icons/
```
# For Ubuntu/Pop!_OS 18.04
sudo apt install gnome-shell-extension-appindicator
```
Then:
```
gnome-shell-extension-prefs
```
And turn on the `KStatusNotifierItem/AppIndicator Support` switch.

4. Launch `barrier`, configure and add to startup application.
