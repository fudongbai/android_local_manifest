Local manifests to build LineageOS 16.0 for [Raspberry Pi 3](http://konstakang.com/devices/rpi3/LineageOS16.0).

How to build:
-------------

1. Set up [Android build environment](https://source.android.com/setup/initializing).

2. Install additional packages:

```
sudo apt-get install kpartx python-mako
```

3. Initialize repo:

```
repo init -u git://github.com/LineageOS/android.git -b lineage-16.0
git clone https://github.com/fudongbai/android_local_manifest .repo/local_manifests -b lineage-16.0
repo sync -c
```

4. Apply [patches](https://github.com/lineage-rpi/android_local_manifest/tree/lineage-16.0/patches):

```
cd path/to/project
git am patchname.patch
```

5. Compile:

```
. build/envsetup.sh
lunch lineage_rpi3-userdebug
mka kernel ramdisk systemimage vendorimage
```

6. Create writable image:

```
cd device/brcm/rpi3
sudo ./mkimg.sh
```
