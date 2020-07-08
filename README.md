# gnuradio
GNU Radio setup and flowcharts

Steps to get GNU Radio with LimeSDR up and running on Ubuntu 20.04. Having spent good amount of time finally this is what worked. Based on steps here: 
https://discourse.myriadrf.org/t/starter-guide-gqrx-gnuradio3-7-soapy-gr-osmo-full-working-ubuntu-18-04/6151

## Initial assumptions and conditions
- GNU Radio has to be 3.7. Tried 3.8 and 3.9 - waste of time.
- Python 2.7, even though it is no longer supported, needs to exist.
- MyRiadRF does not have ppa for Ubuntu 20.04 as of now, so everything needs to be build from source


## Setting up environment

### Prefix
This will be run in PREFIX to keep things clean, so edit ~/.bashrc
```
export LIME_INSTALL=~/LimeSDRInstall/sdr_install/
export LIME_SRC=~/LimeSDRInstall/sdr_src/
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$LIME_INSTALL/lib
export PATH=$PATH:$LIME_INSTALL/bin
```
and create ~/LimeSDRInstall/sdr_install/ and ~/LimeSDRInstall/sdr_src/

### Dependencies
OK, this where the fun starts on 20.04. Not all of these dependencies will have a 20.04 candidate, so they won't be installed, that's OK-ish 
as we will be fixing stuff as we go. With that just sudo up and do:
```
apt-get update 
apt-get -y upgrade 
apt-get -y dist-upgrade
apt-get -y autoremove
apt-get -y install git 
# soapy sdr
apt-get -y install cmake g++ libpython-dev python-numpy swig    
# lime suite
# install core library and build dependencies
apt-get -y install git g++ cmake libsqlite3-dev
# install hardware support dependencies
apt-get -y install libi2c-dev libusb-1.0-0-dev 
# install graphics dependencies
apt-get -y install libwxgtk3.0-dev freeglut3-dev 
# volk
apt-get -y install python-mako python-six libboost-all-dev 
# uhd
apt-get -y install libboost-all-dev libusb-1.0-0-dev python3-mako python3-numpy python3-requests python3-setuptools doxygen python-docutils cmake build-essential
# gnureadio 
apt-get -y install liblog4cpp5-dev liblog4cpp5v5 libgmp3-dev python3-click python3-click-plugins g++ libboost-all-dev libgmp-dev swig python3-numpy python3-mako python3-sphinx python3-lxml doxygen libfftw3-dev libcomedi-dev libsdl1.2-dev libgsl-dev libqwt-qt5-dev libqt5opengl5-dev python3-pyqt5 liblog4cpp5-dev libzmq3-dev python3-yaml
# for GNU Radio Companion + WX & GTK GUI
apt-get -y install python-numpy python-cheetah python-lxml python-gtk2 python-wxgtk3.0 python-numpy python-qt4 python-qwt5-qt4 libqt4-opengl-dev libqwt5-qt4-dev libfontconfig1-dev libxrender-dev libxi-dev 
# gr-osmosdr
apt-get -y install python-cheetah 
# gqrx
apt-get -y install -y qtbase5-dev libqt5svg5-dev 
# gr-foo
apt-get install -y libcppunit-dev
# for limeutil --update, gnuradio
apt-get -y install wget xterm
# pulseaudio
apt-get -y install libpulse-dev pulseaudio
# for sound sink (with alsa):
apt-get -y install alsa-base libasound2 libasound2-dev
```

Additionally install boost if it is not installed yet. I compiled boost_1_71_0 from source and installed it in common, not prefix

## Build and Installation

Sequence is important due to dependencies, so here we go...

### 1. To be continued...




