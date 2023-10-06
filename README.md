# Requirements

## Host
Ubuntu 20
Ubuntu host tools:
- wget
- tar
- build-essential git autoconf bison flex texinfo help2man gawk \
- libtool-bin libncurses5-dev unzip
- qemu-user


Tools Compiled From Source:
- Crosstool ng (1.25)
- Autoconf (2.71) https://www.gnu.org/software/autoconf/


## Target
BeagleBone Black board https://www.beagleboard.org/boards/beaglebone-black
Arm Cortex A8 processor


# Notes:
## Crosstool-ng
- Crosstool-ng was checked out at a specific commit `git checkout 36ad0b1` (Jun 13, 2023)
- configure.ac:4: error: Autoconf version 2.71 or higher is required
    manually installed in `/usr/local/bin/autoconf` (update PATH)

Using sample `arm-cortex_a8-linux-gnueabi`
    FPU = "vfpv3" (https://elinux.org/BeagleBoard_Community) (https://developer.arm.com/documentation/ddi0344/k/programmers-model/vfpv3-architecture)

Toolchain installed at `$HOME/x-tools/arm-training-linux-musleabihf/bin/`
export PATH="${HOME}/x-tools/arm-training-linux-musleabihf/bin/:${PATH}"