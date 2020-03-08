Device configuration for Sony Xperia XZ1 Compact (lilac)
========================================================

Description
-----------

This repository is for LineageOS 16.0 on Sony Xperia XZ1 Compact (lilac).

How to build LineageOS
----------------------

* Make a workspace:

        mkdir -p ~/lineageos/repo
        cd ~/lineageos/repo

* Initialize the repo:

        repo init -u git://github.com/bananafunction/android.git -b lineage-16.0

* Create a local manifest:

        nano .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="bananafunction/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" />
            <project name="bananafunction/android_device_sony_common-treble" path="device/sony/common-treble" remote="github" />
            <project name="bananafunction/android_device_sony_yoshino" path="device/sony/yoshino" remote="github" />
            <project name="bananafunction/android_device_sony_lilac" path="device/sony/lilac" remote="github" />
        </manifest>

* Sync the repo:

        repo sync

* Extract vendor blobs

        cd device/sony/lilac
        ./extract-files.sh

* Setup the environment

        source build/envsetup.sh
        lunch lineage_lilac-userdebug

* Build LineageOS

        make -j8 bacon
