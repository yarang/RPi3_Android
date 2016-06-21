Prerequisites
-------------
```
$ sudo apt-get install gcc-arm-linux-gnueabihf python-mako
```



Prepare the workspace and download sources
------------------------------------------
```
$ mkdir ~/Android-RPi3 && cd ~/Android-RPi3
$ repo init -u git://github.com/Android-RPi3/android_manifest.git -b android-6.0
$ repo sync -jX
```
+ Replace -j**X** with number of core/cpu * 2



Set up ccache and build Android
-------------------------------
```
$ export USE_CCACHE=1
$ export CCACHE_DIR=/your/path/.ccache
$ prebuilts/misc/linux-x86/ccache/ccache -M 50G
$ source build/envsetup.sh
$ lunch rpi3-user
$ make -jX
```
+ Replace -j**X** with number of core/cpu * 2
+ Replace **/your/path/.ccache** with your preferred path



Create SD card
--------------
```
$ ./install.sh -p /dev/sdX
```
+ Replace **X** with proper device number.



#### Community forum:
+ https://groups.google.com/forum/#!forum/android-rpi



#### Thanks to:
+ [peyo-hd](https://github.com/peyo-hd)
+ [RTAndroid](https://github.com/RTAndroid)
+ [kconger](https://github.com/kconger)
