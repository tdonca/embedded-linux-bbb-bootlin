# Requirements

## Host
Ubuntu 20
Ubuntu host tools:
 (basics)
- wget
- tar
 (crosstool-ng requirements)
- build-essential git autoconf bison flex texinfo help2man gawk \
- libtool-bin libncurses5-dev unzip
- qemu-user
  (u-boot requirements)
- libssl-dev device-tree-compiler swig \
- python3-distutils python3-dev python3-setuptools
  (u-boot tftp server requirements)
- tftpd-hpa


Tools Compiled From Source:
- Crosstool ng (1.25)
- Autoconf (2.71) https://www.gnu.org/software/autoconf/


## Target
BeagleBone Black board https://www.beagleboard.org/boards/beaglebone-black
Arm Cortex A8 processor


## Build Environment Setup Steps:
- execute `source ./load-build-env.sh`

## Connect to serial port
- ensure user is added to `dialout` group
- reset pc or execute `newgrp dialout`
- connect with `picocom -b 115200 /dev/ttyUSB0`

# Notes:
## Crosstool-ng
- Crosstool-ng was checked out at a specific commit `git checkout 36ad0b1` (Jun 13, 2023)
- configure.ac:4: error: Autoconf version 2.71 or higher is required
    manually installed in `/usr/local/bin/autoconf` (update PATH)

Using sample `arm-cortex_a8-linux-gnueabi`
    FPU = "vfpv3" (https://elinux.org/BeagleBoard_Community) (https://developer.arm.com/documentation/ddi0344/k/programmers-model/vfpv3-architecture)

Toolchain installed at `$HOME/x-tools/arm-training-linux-musleabihf/bin/`
export PATH="${HOME}/x-tools/arm-training-linux-musleabihf/bin/:${PATH}"

## U-Boot

## Linux Kernel
- Kernel stable git repo: https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/
- Kernel source browser: https://elixir.bootlin.com/linux/latest/source
- Configuration for beagle bone black: `omap2plus_defconfig`
- TI OMAP: https://en.wikipedia.org/wiki/OMAP

Successful kernel load: :)
```
Starting kernel ...

[    0.000000] Booting Linux on physical CPU 0x0
[    0.000000] Linux version 6.1.57 (tudor@tudor-XPS-15-9500) (arm-linux-gcc (crosstool-NG 1.25.0.199_36ad0b1) 12.3.0, GNU ld (crosstool-NG 1.25.0.199_36ad0b1) 2.40) #1 SMP Thu Oct 12 18:02:16 PDT 2023
[    0.000000] CPU: ARMv7 Processor [413fc082] revision 2 (ARMv7), cr=10c5387d
[    0.000000] CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
[    0.000000] OF: fdt: Machine model: TI AM335x BeagleBone Black
```