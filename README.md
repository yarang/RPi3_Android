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



Build kernel
------------
```
$ cd kernel/rpi3
$ export ARCH=arm
$ export CROSS_COMPILE=arm-linux-gnueabihf-
$ scripts/kconfig/merge_config.sh arch/arm/configs/bcm2709_defconfig android/configs/android-base.cfg android/configs/android-recommended.cfg
$ make -jX zImage
$ make -jX dtbs
```
+ Replace -j**X** with number of core/cpu * 2



Create SD card
--------------
```
$ ./install.sh -p /dev/sdX
```
+ Replace **X** with proper device number.

Community forum: https://groups.google.com/forum/#!forum/android-rpi
