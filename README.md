Building AOSP for Hikey with OPTEE OS enabled

This manifest is based on the official AOSP manifest for Hikey. The instructions assume that your
are familiar with building AOSP for the Hikey board.

See the official instructions here:

https://source.android.com/source/devices.html


# Instructions

Getting the source code:
```
$ repo init -u https://github.com/kuscsik/aosp_manifest -b  hikey_optee
$ repo sync
```

Selecting the target platform

```
$ source  build/envsetup.sh
$ lunch hikey-userdebug
```

Building OPTEE OS and Trusted Applications:

```
$ ./optee/build_ta.sh  hikey optee/android_optee_examples.cfg
```

Build Android:

```
# 8GB version of Hikey
$ make -j32 

# 4GB emmc version of Hikey
$ make -j32 TARGET_USERDATAIMAGE_4GB=true
```
