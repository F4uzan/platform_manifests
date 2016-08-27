## Manifest source for AOSP

This is the manifest I use to build AOSP (or anything based on it) for most of my devices, the manifest is highly generic, so it should work with any device you have. Do take a note that it doesn't contain any device-specific tree, which you should probably add in a local manifest.

### Building AOSP using this manifest

#### Initialize this manifest:
repo init -u https://github.com/F4uzan/platform_manifests.git -b android-7.0 (switch android-7.0 to your preferred branch)

#### Sync up the source
repo sync -jX -c (change -jX to the number of task repo should use, and how many download should run simultaneously)

#### Setup the build environment

source build/envsetup.sh

#### Pull up the list of supported device target

lunch

#### Build everything

make otapackage -jX (change -jX to the number of task used by make)

### Finishing the build

The build should be somewhere in out folder, since we're building otapackage, it'll create a zipfile (.zip) instead of system image file (.img), this makes it easier for it to be flashed by custom recoveries.

