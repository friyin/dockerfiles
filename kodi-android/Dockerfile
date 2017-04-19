FROM ubuntu:latest

MAINTAINER Daniel Fernandez "dfmartinez@gmail.com"

RUN \
  apt-get update && \
  apt-get upgrade && \
  apt-get install -y sudo wget apt-utils && \
  apt-get install -y default-jdk && \
  apt-get install -y build-essential default-jdk git curl autoconf unzip zip zlib1g-dev gawk gperf cmake && \
  apt-get install -y lib32stdc++6 lib32z1 lib32z1-dev && \
  apt-get install -y libcurl4-openssl-dev  && \
  mkdir ~/android-sdk-linux && \
  cd && \
  wget https://dl.google.com/android/repository/tools_r25.2.3-linux.zip && \
  cd ~/android-sdk-linux/ && \
  unzip ../tools_r25.2.3-linux.zip  && \
  cd tools/ && \
  ( echo y | ./android update sdk -u -t platform,platform-tool ) && \
  ( echo y | ./android update sdk --all -u -t build-tools-20.0.0 ) && \
  cd && \
  wget https://dl.google.com/android/repository/android-ndk-r12b-linux-x86_64.zip && \
  unzip android-ndk-r12b-linux-x86_64.zip  && \
  cd ~/android-ndk-r12b && \
  cd build/tools/ && \
  ./make-standalone-toolchain.sh --ndk-dir=../../ --install-dir=~/arm-linux-androideabi-4.9-vanilla/android-21 --platform=android-21 --toolchain=arm-linux-androideabi-4.9 && \
  keytool -genkey -keystore ~/.android/debug.keystore -v -alias androiddebugkey -dname "CN=Android Debug,O=Android,C=US" -keypass android -storepass android -keyalg RSA -keysize 2048 -validity 10000 && \
  cd && \
  git clone -b Krypton git://github.com/xbmc/xbmc.git kodi-krypton
