# TWRP Device Tree for Motorola Moto G05, Moto G15 and Moto G15 Power

TWRP device tree for Motorola Moto G05, Moto G15 and Moto G15 Power.

## Build Yourself

Create the TWRP directory:

    mkdir twrp
    cd twrp

Initialize the TWRP source tree:

    repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-14.1

Sync the source:

    repo sync

Clone the device tree:

    git clone https://github.com/Jagatg/android_device_motorola_lamu_twrp.git device/motorola/lamu

Build it:

    source build/envsetup.sh
    lunch twrp_lamu-ap2a-eng
    m vendorbootimage

## Complete Build Commands

    mkdir twrp
    cd twrp

    repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-14.1

    repo sync

    git clone https://github.com/Jagatg/android_device_motorola_lamu_twrp.git device/motorola/lamu

    source build/envsetup.sh

    lunch twrp_lamu-ap2a-eng

    m vendorbootimage

## Build Output

After a successful build, the vendor boot image will be generated at:

    out/target/product/lamu/vendor_boot.img

## Supported Devices

This device tree is for the following devices:

- Motorola Moto G05
- Motorola Moto G15
- Motorola Moto G15 Power

## Device Tree

Device tree path:

    device/motorola/lamu

Device tree repository:

    https://github.com/Jagatg/android_device_motorola_lamu_twrp

## TWRP Source

TWRP source repository:

    https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git

TWRP branch:

    twrp-14.1

## Build Target

    twrp_lamu-ap2a-eng

## Build Command

    m vendorbootimage

## Output Image

    out/target/product/lamu/vendor_boot.img
