1 Development Environment
-------------------------

### 1.1 VirtualBox/Ubuntu OS installation

This section will introduce how to install Ubuntu on Windows OS, ignore this section if your environment is under single OS. Please download from VirtualBox official website ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)) and follow below instructions to install.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image003.jpg)

  

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image004.jpg)

This step will install device driver, please select “Install”:

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image005.jpg)

  

Create virtual machine (Version: Ubuntu 64-Bit):

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image006.jpg)

Select virtual machine memory size:

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image007.jpg)

  

Create virtual machine (If you have an existed Ubuntu image, you can select “Use an existing virtual hard disk file”):

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image008.jpg)

To configure virtual disk space (At least 40GB size):

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image009.jpg)

  

Select Optical drive and using Ubuntu ISO (Ubuntu 12.04/14.04/16.04/18.04 64-bit) startup:

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image010.jpg)

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image011.jpg)

  

### 1.2 Linux environment setup

In order to prevent some complaints in the SDK compilation of the 32 Bits OS, we will use 64 Bits Ubuntu OS as our development environment. The first of all, you should install an Ubuntu based server or Ubuntu on VirtualBox which is introduced in previous section, please download the image from ([http://releases.ubuntu.com/](http://releases.ubuntu.com/12.04.5/)) to get Ubuntu 12.04/14.04/16.04/18.04 Desktop AMD64 version ISO image and use the following instructions to install necessary Ubuntu packages.

**Ubuntu 12.04:**

$ sudo apt-get install bc build-essential libc6-dev libncurses5-dev libgl1-mesa-dev g++-multilib mingw32 tofrodos ia32-libs uboot-mkimage zlib1g-dev mtd-utils vim squashfs-tools gawk cmake cmake-data libstdc++6 device-tree-compiler android-tools-fsutils texinfo libssl-dev python3-crypto python3-pyelftools python3-pycrypto

$ sudo add-apt-repository ppa:nathan-renniewaldock/ppa

$ sudo apt-get update

$ sudo apt-get install liblz4-tool

To install make-4.1 (**This will replace your original /bin/make tool**):

Download [https://ftp.gnu.org/gnu/make/make-4.1.tar.bz2](https://ftp.gnu.org/gnu/make/make-4.1.tar.bz2)

$ tar -jxvf make-4.1.tar.bz2

$ cd make-4.1; ./configure; make -j4

$ make install

**Ubuntu 14.04:**

$ sudo apt-get install bc build-essential libc6-dev lib32ncurses5 libncurses5-dev libncurses5:i386 libgl1-mesa-dev g++-multilib mingw32 tofrodos lib32z1 lib32bz2-1.0 u-boot-tools zlib1g-dev bison libbison-dev flex mtd-utils vim squashfs-tools gawk cmake cmake-data liblz4-tool libmpc3 libstdc++6 device-tree-compiler android-tools-fsutils texinfo libssl-dev python3-crypto python3-pyelftools python3-pycrypto

To install make-4.1 (**This will replace your original /bin/make tool**):

Download [https://ftp.gnu.org/gnu/make/make-4.1.tar.bz2](https://ftp.gnu.org/gnu/make/make-4.1.tar.bz2)

$ tar -jxvf make-4.1.tar.bz2

$ cd make-4.1; ./configure; make -j4

$ make install

**Ubuntu 16.04:**

$ sudo apt-get install bc build-essential libc6-dev lib32ncurses5 libncurses5-dev libncurses5:i386 libgl1-mesa-dev g++-multilib mingw-w64 tofrodos lib32z1 u-boot-tools zlib1g-dev bison libbison-dev flex mtd-utils vim squashfs-tools gawk cmake cmake-data liblz4-tool libmpc3 libstdc++6 device-tree-compiler android-tools-fsutils texinfo libssl-dev python3-crypto python3-pyelftools python3-pycrypto

**Ubuntu 18.04:**

$ sudo apt-get install bc build-essential libc6-dev lib32ncurses5 libncurses5-dev libncurses5:i386 libgl1-mesa-dev g++-multilib mingw-w64 tofrodos lib32z1 u-boot-tools zlib1g-dev bison libbison-dev flex mtd-utils vim squashfs-tools gawk cmake cmake-data liblz4-tool libmpc3 libstdc++6 device-tree-compiler android-tools-fsutils texinfo libssl-dev python3-crypto python3-pyelftools python3-pycrypto

Ubuntu default shell is dash, please reconfigure the default shell with bash:

$ sudo dpkg-reconfigure dash, and choose “No” in the window

Or

$ sudo rm /bin/sh && sudo ln -s /bin/bash /bin/sh

Besides, the openssh-server is used to provide Windows Host PC connected to Linux server and remote building the Linux SDK, and the Samba server is to provide client get Linux SDK image from Linux server.

l $ apt-get install openssh-server

l $ apt-get install samba

l $ vim /etc/samba/smb.conf

o Please reference to related Samba configuration as below: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

Windows Host PC will also need Teraterm or putty to connect to Target board UART2 port with 115200/8/1/n configuration.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image012.png)

Figure 1-1 Linux Development Environment

### 1.3 How to install NT9833x  Linux SDK

Using the following instructions to decompress SDK pack under Linux:

$ tar -jxvf na51090\_linux\_sdk_{version}.tar.bz2

You will get the folder tree as below:

├── na51090\_linux\_sdk?????????????????????? Used to put unpacked SDK source code

├── BSP????????????????????????????????????????? Including linux, busybox, uboot and rootfs source

├── build???????????????????????????????????????? scripts for the environment setup

├── code???????????????????????????????????????? HDAL, linux drivers and sample code

├── configs???????????????????????????????????? Model settings

├── Makefile?????????????????????????????????? Top level Makefile

└── tools????????????????????????????????????????? target board tool

├── toolchains??????????????? ??????????????? Toolchain folder

 ├── aarch64-ca53-linux-gnueabihf-8.4.tar.bz2

└── aarch64-ca53-linux-uclibcgnueabihf-8.4.tar.bz2

### 1.4 How to install Cross compiler

We support both glibc and uclibc cross compiler toolchain, please choose and install it by using below instructions:

$ cd toolchain

$ sudo tar -jxvf aarch64-ca53-linux-gnueabihf-8.4.tar.bz2 -C /opt/arm

or

$ sudo tar -jxvf aarch64-ca53-linux-uclibcgnueabihf-8.4.tar.bz2 -C /opt/arm

2 Introduction to Compilation
-----------------------------

### 2.1 Environment setup

Before each opened a new Terminal window needs to do compiler environment setting, the relevant variables set up, please follow the below instructions to finish it.

$ cd na51090\_linux\_sdk/

$ source build/envsetup.sh

### 2.2 Compilation

Please do a complete compilation for first time.

Select your model:

$ lunch

List your nvt build setting:

??????? $ get\_stuff\_for_environment

Build overall system:

$ make all

  

It will generate the images under na51090\_linux\_sdk/output after the compilation. The details are listed as below.

|\-\- na51090\_linux\_sdk??????????????????????????????? ??????? Put unpacked source code and image

|?? |\-\- Makefile???????????????????????????? ??????? ??????????????? Top level Makefile

|?? |\-\- output???????????????????????????????? ??????? ??????????????? Compiled output images

|????? |\-\- packed???????????????????????? ??????????????? ???????

|????? ???|\-\- FW(SOC)A.bin????????????? ??????? ??????? nvtpack image (All-in-one image)

|????? |\-\- atf.bin ???????????????????????????????? ??????? ??????? ATF image

|????? |\-\- Image.bin???????????????????????????????????????????? Linux Image

|????? |\-\- u-boot.bin???????????????????????????????????????????? uboot image with NVT checksum

|????? |\-\- u-boot.lz.bin???????????????????????????????????????? uboot image (LZ compressed)

|????? |\-\- rootfs.ramdisk.bin?????????????????????????????? ramdisk image (rootfs)

|????? `\-\- rootfs_1.rw.ubifs.bin?????????????????????????? rootfs overlay

  

### 2.3 Top level Makefile

na51090\_linux\_sdk folder has a top level Makefile, it supports many of the make command, such as “make linux” is to compile linux-kernel, “make uboot” can compile u-boot, “make rootfs” can compile root-fs ... and so on, you can use “make help” to find what its commands are supported. Please use top level Makefile to do SDK compilation to avoid some link error occurred. Its help description is as follows:

$ make help

=====================================================

make help???????????? -> show make command info

make all????????????? -> build all

make linux??????????? -> build linux-kernel

make linuxram???????? -> build linux-kernel with ramdisk support

make modules????????? -> build built-in kernel modules

make driver?????????? -> build NVT linux driver modules

make atf????????????? -> build ARM trusted firmware

make uboot??????????? -> build loader(uboot)

make optee_os???????? -> build OPTEE kernel

make optee_client??? ??-> build OPTEE client

make library???????? ??-> build library

make busybox????????? -> build busybox

make rootfs?????????? ?-> build rootfs

make app????????????? -> build applications

make tools??????????? ?-> build tools

make sample?????????? -> build sample code

make post???????????? ?-> run postprocessing script

make pack???????????? -> Generate nvtpack image and preburn images

make publish????????? ?-> remove some sources for publish

=====================================================

make linux_config???? -> config linux-kernel

make linux\_config\_gcov-> modify kernel config for code coverage tool

make uboot_config???? -> config uboot

make busybox_config?? -> config busybox

make linux_header???? -> generate linux-kernel out of tree headers

=====================================================

make clean??????????? -> clean all

make linux_clean ?????-> clean linux-kernel & built-in kernel modules

make driver_clean???? -> clean NVT linux driver modules

make atf_clean??????? -> clean ARM trusted firmware

make uboot_clean????? -> clean loader(uboot)

make optee\_os\_clean?? -> clean optee kernel

make optee\_client\_clean?? -> clean optee client application

make library_clean??? -> clean library

make busybox_clean??? -> clean busybox

make rootfs_clean???? -> clean rootfs

make app_clean??????? -> clean applications

make tools_clean????? -> clean tools

make sample_clean???? -> clean sample code

make post_clean?????? -> run postprocessing clean script

make pack_clean?????? -> Remove nvtpack image

=====================================================  

### 2.4 Project configuration

We provide the following file to control functionalities enable or disable, please refer to the below procedures to configure.

Check model type:

$ get\_stuff\_for_environment

======================================== NVT Setting ======================================== NVT\_PRJCFG\_MODEL\_CFG = /home/user1/na51090\_linux\_sdk/configs/Linux/cfg\_xxx\_NAND\_EVB/ModelConfig.mk

NVT\_PRJCFG\_CFG = Linux

NVT\_PRJCFG\_MODEL_MK =

??????? The ModelConfig.mk will be generated from configs/cfg_gen/nvt-info.dtsi

Enable/disable function:

$ cd na51090\_linux\_sdk/

$ vi configs/cfg_gen/nvt-info.dtsi

To find Linux related options:

/*

?\* Novatek Ltd. BSP part of dts

?*/

/ {

??????? nvt_info {????????????????????????????????????????????? /* Get from ModelConfig.txt */

??????????????? BIN_NAME = "FW98336A";

?? ?????????????BIN\_NAME\_T = "FW98336T";

??????????????? /\* EMBMEM\_BLK\_SIZE, Normally, 2KPageNand=0x20000, 512PageNand=0x4000, SPI=0x10000 */

??????????????? EMBMEM\_BLK\_SIZE = "0x20000";

??????????????? /*

???????????????? \* \[EMBMEM\]

???????????????? \* EMBMEM_NONE

???????????????? \* EMBMEM_NAND

???????????????? \* EMBMEM\_SPI\_NOR

???????????????? \* EMBMEM\_SPI\_NAND

???????????????? \* EMBMEM_EMMC

???????????????? */

??????????????? EMBMEM = " EMBMEM\_SPI\_NAND";

??????????????? /*

???????????????? \* ======= Linux common =========

???????????????? \* application/external

???????????????? */

??????????????? NVT\_CFG\_APP\_EXTERNAL = "dhd\_priv";

??????????????? /\* application include list */

??????????????? NVT\_CFG\_APP = "";

??????????????? /\* rootfs etc folder */

??????? ????????NVT\_ROOTFS\_ETC = "";

??????????????? /\* strip executable binary and library files: yes/no */

??????????????? NVT\_BINARY\_FILE_STRIP = "yes";

??????????????? /\* Using customized kernel config */

??????????????? NVT\_CFG\_KERNEL_CFG = "";

??????????????? /\* Using customized uboot config */

??????????????? NVT\_CFG\_UBOOT_CFG = "";

??????????????? /*

???????????????? \* ======= Linux for different code setting =========

???????????????? \* \[NVT\_LINUX\_SMP\]

???????????????? \* NVT\_LINUX\_SMP_ON

?? ??????????????\* NVT\_LINUX\_SMP_OFF

???????????????? */

??????????????? NVT\_LINUX\_SMP = "NVT\_LINUX\_SMP_ON";

??????????????? /*

???????????????? \* \[NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL\]

???????????????? \* NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL\_DHCP\_SERVER

????????? ???????\* NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL\_DHCP\_CLIENT

???????????????? \* NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL\_STATIC\_IP

???????????????? */

??????????????? NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL = "NVT\_DEFAULT\_NETWORK\_BOOT\_PROTOCOL\_STATIC\_IP";

??????????????? /*

???????????????? \* \[NVT\_ROOTFS\_TYPE\]

???????????????? \* NVT\_ROOTFS\_TYPE\_NAND\_UBI

???????????????? \* NVT\_ROOTFS\_TYPE\_NAND\_SQUASH

???????????????? \* NVT\_ROOTFS\_TYPE\_NAND\_JFFS2

???????????????? \* NVT\_ROOTFS\_TYPE\_NOR\_SQUASH

???????????????? \* NVT\_ROOTFS\_TYPE\_NOR\_JFFS2

???????????????? \* NVT\_ROOTFS\_TYPE_RAMDISK

???????????????? \* NVT\_ROOTFS\_TYPE_EMMC

???????????????? \* NVT\_ROOTFS\_TYPE\_NAND\_SQUASH_NEW

???????????????? */

??????????????? NVT\_ROOTFS\_TYPE = "NVT\_ROOTFS\_TYPE_RAMDISK";

??????????????? /*

???????????????? \* \[NVT_ETHERNET\]

???????????????? \* NVT\_ETHERNET\_NONE

???????????????? \* NVT\_ETHERNET\_EQOS

???????????????? */

??????????????? NVT\_ETHERNET = "NVT\_ETHERNET_EQOS";

??????????????? /*

???????????????? \* \[NVT\_SDIO\_WIFI\]: Remember to update root-fs/rootfs/etc/init.d/S05_Net

???????????????? \* NVT\_SDIO\_WIFI_NONE

???????????????? \* NVT\_SDIO\_WIFI_RTK

???????????????? \* NVT\_SDIO\_WIFI_BRCM

???????????????? \* NVT\_SDIO\_WIFI_NVT

???????????????? */

??????????????? NVT\_SDIO\_WIFI = "NVT\_SDIO\_WIFI_NONE";

??????????????? /*

???????????????? \* \[NVT\_USB\_WIFI\]

???????????????? \* NVT\_USB\_WIFI_NONE

???????????????? */

??????????????? NVT\_USB\_WIFI = "NVT\_USB\_WIFI_NONE";

??????????????? /*

???????????????? \* \[NVT\_USB\_4G\]

???????????????? \* NVT\_USB\_4G_NONE

???????????????? */

??????????????? NVT\_USB\_4G = "NVT\_USB\_4G_NONE";

??????????????? /*

???????????????? \* \[WIFI\_RTK\_MDL\]? : sub item for NVT\_SDIO\_WIFI_RTK

???????????????? \* WIFI\_RTK\_MDL_NONE

???????????????? \* WIFI\_RTK\_MDL_8189

???????????????? */

??????????????? WIFI\_RTK\_MDL = "WIFI\_RTK\_MDL_8189";

??????????????? /*

???????????????? \* \[WIFI\_BRCM\_MDL\]? : sub item for NVT\_SDIO\_WIFI_BRCM

???????????????? \* WIFI\_BRCM\_MDL\_43438a1\_ampk6212axtal26

???????????????? \* WIFI\_BRCM\_MDL\_43455c0\_ampk6255c0

???????????????? */

??????????????? WIFI\_BRCM\_MDL = "WIFI\_BRCM\_MDL\_43438a1\_ampk6212axtal26";

??????????????? /*

???????????????? \* \[WIFI\_NVT\_MDL\]? : sub item for NVT\_SDIO\_WIFI_NVT

???????????????? \* WIFI\_NVT\_MDL_18202

???????????? ????\* WIFI\_NVT\_MDL_18211

???????????????? */

??????????????? WIFI\_NVT\_MDL = "WIFI\_NVT\_MDL_18211";

??????????????? /*

???????????????? \* \[NVT\_CURL\_SSL\]

???????????????? \* NVT\_CURL\_SSL_OPENSSL

???????????????? \* NVT\_CURL\_SSL_WOLFSSL

???????????????? */

??????????????? NVT\_CURL\_SSL = "NVT\_CURL\_SSL_OPENSSL";

??????????????? /*

???????????????? \* \[NVT\_UBOOT\_ENV\_IN\_STORG_SUPPORT\]

???????????????? \* NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT\_NAND

???????????????? \* NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT\_NOR

???????????????? \* NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT\_MMC

???????????????? \* NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT\_OFF

???????????????? */

??????????????? NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT = "NVT\_UBOOT\_ENV\_IN\_STORG\_SUPPORT_OFF";

??????? };

};

3 Build U-boot
--------------

### 3.1 Compilation

The Uboot source code is placed on “na51090\_linux\_sdk/u-boot”, typing “make uboot” can be used to compile Uboot, and we provide two images are u-boot.bin(non-compressed) and u-boot.lz.bin(compressed) under na51090\_linux\_sdk/output.

U-boot build:

$ cd na51090\_linux\_sdk/

$ make uboot

U-boot config:

$ cd na51090\_linux\_sdk/

$ make uboot_config

U-boot clean build:

$ make uboot_clean

### 3.2 User customization

The uboot have two config files will have different configured properties. One is for common function, the other is for the low level setting.

The low level setting can modify this file “include/configs/nvt-na51090-evb-a64.h” directly when you have request for the Uboot related configuration.

e.g. Uboot passed to Linux’s cmdline can be changed with this variable

#define CONFIG\_USE\_BOOTARGS

#define CONFIG\_BOOTARGS\_COMMON??? ??"earlycon=nvt\_serial,0x2f0280000 rootwait console=ttyS0,115200 debug\_boot\_weak\_hash? "

#define CONFIG\_BOOTARGS????????????? ?CONFIG\_BOOTARGS_COMMON "root=/dev/ram0 rootfstype=ramfs rdinit=/linuxrc "

Please reference to “SDK\_UBoot\_Programming\_Guide\_en” for more details.

4 Build Kernel Code
-------------------

### 4.1 Compilation

The Linux kernel source code is placed on “na51090\_linux\_sdk/linux-kernel”, typing “make linux” can be used to compile Linux kernel, and the image name is Image.bin under na51090\_linux\_sdk.

$ cd na51090\_linux\_sdk/

$ make linux

Linux clean build:

$ make linux_clean

### 4.2 System configuration

#### 4.2.1 Menu configuration

Top Makefile is already integrated the formal Linux menuconfig, to use the following instruction can do the function selection. Please avoid using formal Linux “make menuconfig” under linux-kernel directly; it will cause error because the important variables are not set correctly.

$ make linux_config

Choose “Save” after finished function selection; it can generate a new _.config_ for the Linux compilation usage.

NA51090 SDK provides two Kernel configuration file under “na51090\_linux\_sdk/BSP/linux-kernel/arch/arm64/configs/”, one is for the debug mode, and the other is for the release mode.

l na51090\_XXX\_defconfig_debug, the debug mode will enable most of the functions for the development stage

l na51090\_XXX\_defconfig_release, the release mode will only enable boot necessary parts.

Edit Top Makefile to switch the configuration file:

$ cd na51090\_linux\_sdk/

$ vi Makefile

\# kernel & modules

CUSTBOARDCONFIG := $(strip $(shell echo $(NVT\_PRJCFG\_MODEL\_CFG) | grep NVT\_CFG\_KERNEL\_CFG | awk -F'=' '{print $$NF;}'))

ifeq ($(EMBMEM), EMBMEM\_SPI\_NOR)

#BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_nor_debug; fi)

BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_nor_release; fi)

else ifeq ($(EMBMEM), EMBMEM_EMMC)

#BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_emmc_debug; fi)

BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_emmc_release; fi)

else

#BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_debug; fi)

BOARDCONFIG := $(shell if \[ ! -z $(NVT\_CFG\_KERNEL\_CFG) \]; then echo $(NVT\_CFG\_KERNEL\_CFG); else echo $(SDK\_CODENAME)\_evb\_defconfig\_release; fi)

endif

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image013.jpg)

Figure 4-1 Menu configuration

  

#### 4.2.2 Device tree

The device tree can be generated by dtc(device tree compiler) tool as below, you can find the *.dtsi in “na51090\_linux\_sdk/configs/cfg\_xxx” and users can set command “make cfg” at “na51090\_linux\_sdk/”. Config items detail description put at na51090\_linux_sdk/configs/doc. It can be used to compile device tree, and we will output image nvt-evb.dtb under  na51090\_linux\_sdk/output.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image014.png)

  

The merge method is Union, for example:

configs/cfg_gen/nvt-basic.dtsi

User can modify CPU clock-frequency from 1200000000(1.2GHz) to 1000000000(1GHz), or 1100000000(1.1GHz), or 1300000000(1.3GHz), or 1350000000(1.35GHz), and compiler again. Users can use new image to boot at new CPU clock-frequency.

#include &lt;dt-bindings/gpio/gpio.h&gt;

#include &lt;dt-bindings/interrupt-controller/arm-gic.h&gt;

/ {

???? model = "Novatek NA51090";

???? compatible = "novatek,na51090", "nvt,ca53";

???? interrupt-parent = &lt;&gic&gt;;

???? #address-cells = &lt;2&gt;;

???? #size-cells = &lt;2&gt;;

???? psci {

???????? compatible = "arm,psci-0.2";

???????? method = "smc";

???? };

???? cpus {

???????? #address-cells = &lt;2&gt;;

???????? #size-cells = &lt;0&gt;;

???????? cpu0: cpu@0 {

????????????? device_type = "cpu";

????????????? compatible = "arm,cortex-a53", "arm,armv8";

????????????? reg = &lt;0x0 0x0&gt;;

????????????? next-level-cache = &lt;&A53_L2&gt;;

????????????? clock-frequency = &lt;1200000000&gt;;

????????????? enable-method = "psci";

???????? };

???????? cpu1: cpu@1 {

????????????? device_type = "cpu";

????????????? compatible = "arm,cortex-a53", "arm,armv8";

????????????? reg = &lt;0x0 0x1&gt;;

????????????? next-level-cache = &lt;&A53_L2&gt;;

????????????? clock-frequency = &lt;1200000000&gt;;

????????????? enable-method = "psci";

???????? };

???????? cpu2: cpu@2 {

????????????? device_type = "cpu";

????????????? compatible = "arm,cortex-a53", "arm,armv8";

????????????? reg = &lt;0x0 0x2&gt;;

????????????? next-level-cache = &lt;&A53_L2&gt;;

????????????? clock-frequency = &lt;1200000000&gt;;

????????????? enable-method = "psci";

???????? };

???????? cpu3: cpu@3 {

????????????? device_type = "cpu";

????????????? compatible = "arm,cortex-a53", "arm,armv8";

????????????? reg = &lt;0x0 0x3&gt;;

????????????? next-level-cache = &lt;&A53_L2&gt;;

????????????? clock-frequency = &lt;1200000000&gt;;

????????????? enable-method = "psci";

???????? };

???????? A53_L2: l2-cache0 {

????????????? compatible = "cache";

???????? };

???? };

????? …

configs/cfg_gen/nvt-peri.dtsi

#include &lt;dt-bindings/gpio/nvt-gpio.h&gt;

#include "nvt-basic.dtsi"

/ {

???? chosen {

???????? bootargs = " ";

???????? stdout-path = "serial0:115200n8";

???? };

???? aliases {

???????? serial0 = &uart0;

???????? serial1 = &uart1;

???????? serial2 = &uart2;

???????? serial3 = &uart3;

???????? serial4 = &uart4;

???????? mmc0 = &mmc0;? /* Fixed to mmcblk0 for sdio1 */

???? };

???? uart0: uart@f0280000 {

???????? compatible = "ns16550a";

???????? reg = &lt;0x2 0xf0280000 0x0 0x1000&gt;;

???????? interrupts = &lt;GIC\_SPI 43 IRQ\_TYPE\_LEVEL\_HIGH&gt;;

???????? baud = &lt;115200&gt;;

???????? reg-shift = &lt;2&gt;;

???????? reg-io-width = &lt;4&gt;;

???????? no-loopback-test = &lt;1&gt;;

???????? clock-frequency = &lt;24000000&gt;;

???????? rx\_trig\_level = &lt;3&gt;;

???????? hw_flowctrl = &lt;0&gt;;

???? };

???? uart1: uart@f0290000 {

???????? compatible = "ns16550a";

???????? reg = &lt;0x2 0xf0290000 0x0 0x1000&gt;;

???????? interrupts = &lt;GIC\_SPI 44 IRQ\_TYPE\_LEVEL\_HIGH&gt;;

???????? baud = &lt;115200&gt;;

???????? reg-shift = &lt;2&gt;;

???????? reg-io-width = &lt;4&gt;;

???????? no-loopback-test = &lt;1&gt;;

???????? clock-frequency = &lt;48000000&gt;;

???????? rx\_trig\_level = &lt;3&gt;;

???????? hw_flowctrl = &lt;0&gt;;

???? };

???? uart2: uart@f02a0000 {

???????? compatible = "ns16550a";

???????? reg = &lt;0x2 0xf02a0000 0x0 0x1000&gt;;

???????? interrupts = &lt;GIC\_SPI 45 IRQ\_TYPE\_LEVEL\_HIGH&gt;;

???????? baud = &lt;115200&gt;;

???????? reg-shift = &lt;2&gt;;

???????? reg-io-width = &lt;4&gt;;

???????? no-loopback-test = &lt;1&gt;;

???????? clock-frequency = &lt;48000000&gt;;

???????? rx\_trig\_level = &lt;3&gt;;

???? };

???? uart3: uart@f02b0000 {

???????? compatible = "ns16550a";

???????? reg = &lt;0x2 0xf02b0000 0x0 0x1000&gt;;

???????? interrupts = &lt;GIC\_SPI 38 IRQ\_TYPE\_LEVEL\_HIGH&gt;;

???????? baud = &lt;115200&gt;;

???????? reg-shift = &lt;2&gt;;

???????? reg-io-width = &lt;4&gt;;

???????? no-loopback-test = &lt;1&gt;;

???????? clock-frequency = &lt;48000000&gt;;

???????? rx\_trig\_level = &lt;3&gt;;

???? };

???? uart4: uart@f02c0000 {

???????? compatible = "ns16550a";

???????? reg = &lt;0x2 0xf02c0000 0x0 0x1000&gt;;

???????? interrupts = &lt;GIC\_SPI 47 IRQ\_TYPE\_LEVEL\_HIGH&gt;;

???????? baud = &lt;115200&gt;;

???????? reg-shift = &lt;2&gt;;

???????? reg-io-width = &lt;4&gt;;

???????? no-loopback-test = &lt;1&gt;;

???????? clock-frequency = &lt;48000000&gt;;

???????? rx\_trig\_level = &lt;3&gt;;

???? };

  

#### 4.2.3 Partition table

The Nand/EMMC driver of kernel will do for the set partition initialization process as shown below, Uboot will read the partition info(nvt-storage-partition.dtsi) from dts, and then the Kernel also read it from dts to do basic initialization.

If you want to change flash partition size or add a partition, please configure device tree nvt-storage-partition.dtsi and build dtb image, burn into flash or load to dram again(default address at 0x1f00000).

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image015.png)

Figure 4-2 Partition initialization

SPI NAND partition example:

nvt-storage-partition.dtsi for flash partition

&nand {

???? partition_loader {????? label = "loader";?????? reg = &lt;0x0 0x0000000 0x0 0x40000&gt;; }; /* Fixed */

???? partition_fdt {???? ??????? label = "fdt";??? ??????? reg = &lt;0x0 0x40000?? 0x0 0x40000&gt;; }; /* Fixed */

???? partition_fdt.restore {? label = "fdt.restore";?? reg = &lt;0x0 0x80000?? 0x0 0x40000&gt;; }; /* Fixed */

???? partition_atf {???????? label = "atf";????????? reg = &lt;0x0 0x0C0000? 0x0 0x40000&gt;; };

???? partition_uboot {?????? label = "uboot";??????? reg = &lt;0x0 0x100000? 0x0 0x1C0000&gt;; };

???? partition_uenv {??????? label = "uenv";???????? reg = &lt;0x0 0x2C0000? 0x0 0x40000&gt;; };

???? partition_kernel {????? label = "kernel";?????? reg = &lt;0x0 0x300000? 0x0 0x0500000&gt;; };

???? partition_rootfs {????? label = "rootfs";?????? reg = &lt;0x0 0x800000? 0x0 0x5100000&gt;; };

???? partition_rootfs1 {???? label = "rootfs1";????? reg = &lt;0x0 0x5900000 0x0 0x2700000&gt;; };

};

If you want to change the partition size or add a partition, please configure it from the dts info. If users want to add user partition such as app1, users can add such as follow:

partition\_app1 {? ? label = "app1";????????? reg = &lt;0x0 start\_addr 0x0 size&gt;; };

### 4.3 Debug

To debug the Kernel, you will need System.map or objects for the debug symbol loading, please get them from “linux-kernel/” as shown below:

|\-\- linux-kernel

|?????? ??????? |\-\- Makefile

|?????????????? |\-\- Module.symvers

|?????????????? |\-\- System.map

|?????????????? |\-\- arch

|?????????????? |\-\- block

|?????????????? |\-\- crypto

|?????????????? |\-\- drivers

|?????????????? |\-\- firmware

|?????????????? |\-\- fs

|?????????????? |\-\- include

|?????????????? |\-\- init

|?????????????? |\-\- ipc

|?????????????? |\-\- kernel

|?????????????? |\-\- lib

|?????????????? |\-\- mm

|?????????????? |\-\- modules.builtin

|?????????????? |\-\- modules.order

|?????????????? |\-\- net

|?????????????? |\-\- scripts

|?????????????? |\-\- security

|?????????????? |\-\- sound

|?????????????? |\-\- source

|?????????????? |\-\- usr

|?????????????? |\-\- vmlinux

|?????????????? `\-\- vmlinux.o

To add more debug information, we can turn on CONFIG\_DEBUG\_INFO option before compiling Linux kernel as below.

“Kernel Hacking > Compile-time checks and compiler options > Compile the kernel with debug info”

$ cd na51090\_linux\_sdk/

$ make linux_config

Rebuild all; this binary will contain debug symbol information.

|\-\- linux-kernel

|?????? ??????? |\-\- vmlinux

5 Build Kernel Modules
----------------------

In addition to build-in drivers, Linux had also provided an external load mode called Kernel module, can be loaded by “modprobe” or “insmod”. The below will introduce to build-in modules and the out-of-tree modules.

### 5.1 Build-in module compilation

Typing “make modules” under na51090\_linux\_sdk can do build-in modules compilation and install path is root-fs/rootfs/lib/modules/{KER_VER}/kernel/.

$ cd na51090\_linux\_sdk/

$ make modules

  

### 5.2 Out-of-Tree module compilation

This folder under “na51090\_linux\_sdk/code” provides NVT platform drivers, typing “make supplement” to do the Out-of Tree modules compilation as below. And the modules will be installed on na51090\_linux\_sdk/BSP/root-fs/rootfs/lib/modules/{KER_VER}/extra/.

$ cd na51090\_linux\_sdk/

$ make driver

Linux Out-of-Tree driver module clean build:

$ make driver_clean

### 5.3 HDAL

HDAL is the hardware abstraction layer driver and sample code, this one can be used to build proprietary driver modules, such as video process, video capture and video codec…etc. We provide the following instructions to build.

??????? $ make hdal

Clean build:

??????? $ make hdal_clean

Please refer to the other documents for details.

### 5.4 Installation

The modules can be installed by “modprobe” or “insmod/rmmod” to install or uninstall, besides the modprobe will also install related modules automatically.

Example:

1. modprobe (Only needs the module name)

modprobe ehci-hcd

2. insmod/rmmod (This method needs a full path)

insmod /lib/modules/{KER_VER}/extra/crypto/cryptodev-linux/cryptodev.ko

6 Build tools
-------------

This folder will integrate some Linux open source tools as the following description:

htop????????????????? - Linux process monitoring, to provide more than top information

gdb?????????????????? - gdb server for the application debug

ethtool????????????? - Utility for controlling network drivers and hardware

bonnie++???????? - A benchmark suite that is aimed at performing a number of simple tests of hard drive and file system performance

memtester??????? - A userspace utility for testing the memory subsystem for faults

mtd-utils?????????? - MTD device utilities

procps????????????? - A tool set to provide system analysis tools (vmstat, slabtop,…etc)

stress??????????????? - System performance testing tool

stress-ng????????? - Advanced system performance testing tool

sdcard_test.sh- To do sd driver r/w testing

iozone????????????? - IO r/w performance testing

VDBench???????? - CPU/io performance testing

### 6.1 Compilation

To select the tools what you want: mtd-utils, memtester, bonnie, ethtool, gdb, htop, netperf, iperf and procps and running below instructions:

e.g.

$ cd na51090\_linux\_sdk/

$ cd tools/

$ make stress

Tools clean build:

$ make clean

### 6.2 Installation

$ make install

The tools will be installed on “na51090\_linux\_sdk/BSP/root-fs”.

7 Build root-fs
---------------

### 7.1 Introduction

The root file system will be mounted by Linux kernel, the first process of the kernel is /sbin/init (PID=1). We provide several root file systems support for selection, the following are the summary features:

l UBIFS: readable/writable file system, support Nor and Nand flash, fast mounting speed, best bad block management and better IO performance. Suitable for low memory size and large flash size use condition.

We have a detail introduction in OSDRV/NT9833x\_UBI\_Filesystem\_User\_Guide_en.doc

l Squashfs: read-only file system, high compression rate. Suitable for small size flash and readonly use condition.

l JFFS2: It is a log-structured file system which can support Nand and Nor flash devices. Providing zlib, lzo and rtime compression methods. Suitable for small flash size and readable/writable use condition.

l RAMDISK: To provide a ram based file system.

  

### 7.2 Configuration

The root file system will generate Nand flash type image format, we support squashfs and ubifs, please follow the Nand flash specification to modify the parameters:

$ cd na51090\_linux\_sdk/BSP/root-fs/

$ vi ubi\_max\_leb.py

To find below lines:

W = 1024

SP = 128 * 1024

SL = 124 * 1024

According the Nand flash to modify the parameters:

l W is the entire flash chip Physical eraseblocks numbers

l SP is the Size of block page

l SL= (Size of block -2) * Size of page.

e.g.

128MB Nand flash = 1024 eraseblocks = 1024 * 128KB

W = 1024

SP = 64 * 2048 = 128 * 1024

SL = (64 – 2) * 2048 = 124 * 1024

$ vi mtd_cfg.txt

??????? We can support two mtd\_cfg.txt in BSP/root-fs/ and configs/cfg\_gen, the build tool will search configs/cfg\_gen/mtd\_cfg.txt firstly, and the second is BSP/root-fs/mtd_cfg.txt.

To find below lines:

ROOTFS\_UBI\_SUB\_PAGE\_SIZE=2048????????? # Same as page size

ROOTFS\_UBI\_PAGE_SIZE=2048???? ???????? # Nand page size

ROOTFS\_UBI\_ERASE\_BLK\_SIZE=126976?????? # (64-2) * Page size=126976

ROOTFS\_UBI\_MAX\_LEB\_COUNT=361?????????? # Size = UBI\_MAX\_LEB\_COUNT * UBI\_BLK\_SIZE; It's calculated by "python ubi\_max_leb.py Bytes"

ROOTFS\_UBI\_RW\_MAX\_LEB\_COUNT=258???????????? # Size = UBI\_MAX\_LEB\_COUNT * UBI\_BLK\_SIZE; It's calculated by "python ubi\_max\_leb.py Bytes"

ROOTFS\_UBI\_BLK_SIZE="128KiB"?????????? # UBIFS Nand flash block size (KiB)

ROOTFS\_UBI\_COMPRESS\_MODE="lzo"????????????? # UBIFS compression type: "lzo", "favor\_lzo", "zlib" "none"

ROOTFS\_SQ\_COMPRESS_MODE="xz"?????????? # Squashfs compression type: "gzip", "lzo" and "xz"

ROOTFS\_SQ\_BLK_SIZE="128K"????????????? # Squashfs Nand flash block size (KiB): e.g. spinand: 128K, spinor: 64K

ROOTFS\_JFFS2\_COMPRESS_MODE="lzo"?????? # jffs2 compression type: "lzo" "zlib" "rtime"

ROOTFS\_JFFS2\_SIZE=0x3200000??????????? # jffs2 partition size: get from /proc/mtd

ROOTFS\_JFFS2\_RW_SIZE=0x2500000????????????? # jffs2 partition size: get from /proc/mtd

ROOTFS\_JFFS2\_BLK_SIZE="128KiB"????????????? # jffs2 block size (KiB): spinand: 128KiB, spinor: 64KiB

ROOTFS\_JFFS2\_PAGE_SIZE="2048"????????? # jffs2 page size (Bytes): only used by nand, nor flash can be ignored.

ROOTFS\_EXT4\_SIZE=$(shell printf "%d\\n" 0x0A000000)

ROOTFS\_FAT\_CACHE_SIZE=$(shell printf "%d\\n" 0x0A000000)

#APPFS

ROOTFS\_JFFS2\_APP_SIZE=0x01E0000

ROOTFS\_JFFS2\_APP\_NOR\_SIZE=0x0E20000

ROOTFS\_UBI\_APP\_MAX\_LEB_COUNT=231

The necessary parameters need to be modified as below description:

l ROOTFS\_UBI\_SUB\_PAGE\_SIZE: The sub-page size of the Nand flash

l ROOTFS\_UBI\_PAGE_SIZE: The page size of the Nand flash

l ROOTFS\_UBI\_ERASE\_BLK\_SIZE: (Nand flash block size – 2) * Page size

l ROOTFS\_UBI\_MAX\_LEB\_COUNT: Use ubi\_max\_leb.py to calculate it

$ Usage: ubi\_max\_leb.py PartitionSize (Bytes)

l ROOTFS\_UBI\_RW\_MAX\_LEB\_COUNT: Use ubi\_max_leb.py to calculate it

$ Usage: ubi\_max\_leb.py PartitionSize (Bytes)

l ROOTFS\_UBI\_BLK_SIZE: Nand flash block size

l ROOTFS\_UBI\_COMPRESS_MODE: Compression method = LZO

l ROOTFS\_SQ\_COMPRESS_MODE: Squashfs compression mode

l ROOTFS\_SQ\_BLK_SIZE: Squashfs nand flsh block size

l ROOTFS\_JFFS2\_COMPRESS_MODE: jffs2 compression type: "lzo" "zlib" "rtime"

l ROOTFS\_JFFS2\_SIZE: Rootfs partition size

l ROOTFS\_EXT4\_SIZE: EMMC boot partition size

l ROOTFS\_FAT\_CACHE_SIZE: EMMC boot FAT partition size (Optional)

l ROOTFS\_JFFS2\_APP_SIZE: The size of the app partition in nand flash

l ROOTFS\_JFFS2\_APP\_NOR\_SIZE: The size of the app partition in nor flash

l ROOTFS\_UBI\_APP\_MAX\_LEB\_COUNT: The ubi image size in app partition (Use ubi\_max_leb.py to calculate it)

You can modify the ubi mount parameters with your requirement, e.g.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image016.jpg)

  

BSP/root-fs/ubi\_max\_leb.py

def get\_ubifs\_max\_leb(partition\_size):????????? #Unit: Bytes

??????? P = partition_size/SP

??????? BR = math.ceil(**30** \* W/float(1024))????? # Sync with kernel

??????? B = max(BB, BR)

??????? ubi_overhead = (( B - BB + 4 ) * SP + O * ( P - B - 4 ))/float(SP)

? ??????ubi\_overhead = math.ceil(ubi\_overhead)

??????? ubi\_overhead = math.floor(((P - ubi\_overhead) * SP) / float(SL))

???? ? if ubi_overhead < 0:

???????? return -1

???? ? else:

???????? return (ubi_overhead - 1)

Note: linux menuconfig Maximum expected bad eraseblock count per 1024 eraseblocks value “30” must be the same with ubi\_max\_leb.py value “30”. This parameter will affect the bad block management, please reserve enough blocks(e.g. 10, 20) per 1024 erase blocks.

### 7.3 Modify flash filesystem partition size

Users must check mtd config definiton in configs/cfg\_gen/mtd\_cfg.txt, the parameters: ROOTFS\_UBI\_MAX\_LEB\_COUNT, ROOTFS\_UBI\_RW\_MAX\_LEB\_COUNT and ?ROOTFS\_UBI\_APP\_MAX\_LEB\_COUNT value must use ubi\_max\_leb.py to calculate.

  

### 7.4 Compilation

Using “make rootfs” instruction to generate rootfs bin, the image type can be selected by nvt-info.dtsi in configs folder. They can be produced into “na51090\_linux\_sdk/output/rootfs.ubifs.bin”, “na51090\_linux\_sdk/output/rootfs.squash.bin” and “na51090\_linux\_sdk/output/rootfs.jffs2.bin” separately. The command “mr” also can be used to compile rootfs if you are not in na51090\_linux\_sdk root folder.

$ cd na51090\_linux\_sdk/

$ source build/envsetup.sh

$ make rootfs

Rootfs clean build:

$ make rootfs_clean

This command will remove busybox tools, kernel modules…etc., please follow below procedure to generate rootfs image:

$ make busybox

$ make app ($ make library if necessary)

$ make hdal

$ make rootfs

  

### 7.5 Folder description

l **Architecture**

|     |     |
| --- | --- |
| Folder | Description |
| bin | User binaries |
| dev | Device files |
| etc | System management configuration files |
| home | User home directories |
| init -> bin/busybox | It is used to kernel boot necessary init process, for the initial environment setup. |
| lib | Standard system libraries |
| linuxrc -> bin/busybox |     |
| mnt | External storage device mount folder (/mnt/sd, /mnt/usb) |
| proc | RAM based FS to provide process information |
| root | Root’s folder (The default shell will login here) |
| sbin | System management binaries |
| srv | Service data |
| sys | RAM based FS to provide user space and kernel space attribute/properties link. |
| tmp | RAM based temp folder |
| usr | User libraries, binaries |
| var | Service log message, including kernel, application, web server default folder(/var/www) and service…etc |

l **/etc/passwd**

This file can setup user account environment, below is to introduce how to enable login password.

$ vi /etc/inittab

::respawn:-/bin/login

Replace “::respawn:-/bin/login -f root” with “::respawn:-/bin/login” as below

Fill in the red part with the encryption password which can be generated by openssl tool:

$ vi /etc/passwd

root:EncryptionCode:0:0:root:/root:/bin/sh

Openssl generation:

$ openssl passwd -crypt YourPWD

l **/etc/init.d**

System will execute the following shell scripts according sequence.

rcS -> S00\_PreReady -> S05\_Net -> S10\_SysInit -> S10\_hdal\_init -> S99\_Sysctl

Moreover, power off will execute deinitialization process as below.

rcK -> K00\_Sys -> K99\_Sys

l **/etc/sysctl.conf**

This file is handle sysctl parameters setup.

### 7.6 UBIFS

The UBIFS is our default rootfs format, UBIFS (Unsorted Block Image File System) was originally called JFFS3, is JFFS2 next generation version. The main capabilities are faster mounting, quicker access to large files, and improved write speeds. UBIFS also preserves or improves upon JFFS2's on-the-fly compression, recoverability and power fail tolerance, and data compression allows zlib or LZO. The filename is UBI.IMG after compilation.

### 7.7 Squashfs

Squashfs is a read-only file system which can support gzip, lzo and xz compression modes. The main features are high compression rate, stores full 32bits uid/gids and creation time, support block size up to 1Mbytes. The filename is SQ_ROOTFS.IMG after compilation.

### 7.8 Jffs2

JFFS2 was developed by Red Hat, based on the work started in the original JFFS by Axis Communications, AB, it is a readable and writable file system. JFFS2 will scan rootfs partition during mounting; the mount time depends on the rootfs size. The main features are listed as below:

l Support compression mode

l Mounting time will be affected by flash size

l Not support all Nand flash devices with HW ecc, please refer to Linux driver application note

The filename is rootfs.jffs2.bin after compilation.

For the kernel configuration to add jffs2 support, you must add below configurations:

File systems

-\> Miscellaneous filesystems

-\> \[*\] Journalling Flash File System v2 (JFFS2) support

-\> \[*\] Advanced compression options for JFFS2

-\> \[*\] JFFS2 LZO compression support

For the uboot configuration to choose root file system type, please refer to the UBoot\_Programing\_Guide.

### 7.9 HDAL sample code

We will pack one partition named DVR\_xxx.bin is under na51090\_linux\_sdk/configs/Linux/cfg\_xxx/nvt-nvtpack.dtsi partition\_name = "app" field. You could modify the partition size and recalculate the related parameters to fill in the nvt -storage-partition.dtsi partition\_app field.

Please refer to 7.2 for mtd_cfg.txt description.

  

8 Build App
-----------

### 8.1 Compilation

NVT platform needs the necessary applications to perform the requested actions, please using below instructions to compile (This part doesn’t provide source code).

$ cd na51090\_linux\_sdk/code/application

$ make install

Please execute “source build/envsetup.sh” firstly when you start to build it. Please reference to Application Note for the other details.

We have fine-tuned some functions and the fpu related setting, please add $(PLATFORM_CFLAGS) to your Makefile to get more performance.

e.g.

nvt02854@oaalnx13:~/na51090\_linux\_sdk/na51090\_linux\_sdk$ get\_stuff\_for_environment

======================================== NVT Setting ========================================

NVT\_PRJCFG\_CFG = Linux

NVT\_PRJCFG\_MODEL\_CFG = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk/configs/Linux/cfg\_TEST\_FPGA\_a64/ModelConfig.mk

LINUX\_BUILD\_TOP = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk

UBOOT\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/BSP/u-boot

OPTEE\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/BSP/optee

KERNELDIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk/BSP/linux-kernel

BUSYBOX\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/BSP/busybox

TOYBOX\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/BSP/toybox

ROOTFS\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/BSP/root-fs

APP\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/code/application

LIBRARY\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/code/lib

INCLUDE\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/code/lib/include

NVT\_DRIVER\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk/code/driver

NVT\_HDAL\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk/code/hdal

NVT\_VOS\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux\_sdk/code/vos

NVT\_RTOS\_MAIN\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/code/rtos-main

SAMPLE\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/code/sample

TOOLS\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/tools

OUTPUT\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/output

LOGS\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/logs

BUILD\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/build

CONFIG\_DIR = /home/nvt02854/na51090\_linux\_sdk/na51090\_linux_sdk/configs

PLATFORM\_CFLAGS = -march=armv8-a -mtune=cortex-a53 -ftree-vectorize -fno-builtin -fno-common -Wformat=1 -D\_BSP\_NA51090\_

PLATFORM\_AFLAGS = march=armv8-a -mtune=cortex-a53 -D\_BSP\_NA51090\_

NVT_HOST = aarch64-ca53-linux-uclibc

LINUX\_CPU\_TYPE = cortex-a53x64

NVT\_LINUX\_VER = 4.19.148

NVT\_MULTI\_CORES_FLAG = -j80

CROSS_COMPILE = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-

CROSS\_TOOLCHAIN\_PATH = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4

CROSS\_TOOLCHAIN\_BIN_PATH = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin

SYSROOT_PATH = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/aarch64-ca53-linux-uclibc/sysroot

UBOOT\_CROSS\_COMPILE = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-

AS = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-as

CC = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-gcc

CXX = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-g++

LD = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-ld

LDD = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-ldd

AR = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-ar

NM = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-nm

GDB = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-gdb

STRIP = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-strip

OBJCOPY = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-objcopy

OBJDUMP = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin/aarch64-ca53-linux-uclibc-objdump

PATH = /opt/CEVA-ToolBox/V17/XM4/CEVA-XM4:/opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/bin:/opt/utility/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/snap/bin:.

LD\_LIBRARY\_PATH = /opt/ivot/aarch64-ca53-linux-uclibcgnueabihf-8.4/usr/local/lib

=============================================================================================

  

9 Build Libraries
-----------------

### 9.1 Compilation

na51090\_linux\_sdk provides some proprietary libraries and header files for the product customization (this part doesn’t involve source code, we only provide you *.so), please according the following instruction to compile it.

$ cd na51090\_linux\_sdk/

$ make library

Libraries clean build:

$ make library_clean

Please execute “source build/envsetup.sh” firstly when you start to build it. Please reference to Application Note for the other details.

  

10 Build busybox
----------------

### 10.1 Compilation

Busybox can provide rootfs necessary tools, using below instruction can compile it. And the tools will be installed to na51090\_linux\_sdk/BSP/root-fs.

$ cd na51090\_linux\_sdk/

$ make busybox

mybusybox clean build:

$ make busybox_clean

### 10.2 Menu configuration

SDK will provide two busybox configuration files, one is normal version (busybox\_cfg\_normal), and the other is minimized version (busybox\_cfg\_small). Edit Top Makefile can change the busybox configuration, the default is normal version.

Edit Top Makefile to switch the configuration file:

$ cd na51090\_linux\_sdk/

$ vi Makefile

BUSYBOX\_CFG:=busybox\_cfg_full

#BUSYBOX\_CFG:=busybox\_cfg_small

Below instruction can handle busybox features selection:

$ make busybox_config

Choose “Exit/Save” after you finished function selection, it can generate new .config for the Busybox compilation usage.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image017.jpg)

  

11 Build sample code
--------------------

### 11.1 Compilation

The device driver testing applications will be used to test NVT peripheral devices; the following instructions can compile it. And it will be installed to na51090\_linux\_sdk/BSP/root-fs.

$ cd na51090\_linux\_sdk/

$ make sample

Driver test clean build:

??????? $ make sample_clean

  

12 Update Firmware
------------------

We provide two OS version nvtpack image could be used, one is Linux version will be generate by Linux version nvtpack tool, the images will be generated under the output folder. Another is Windows vesion nvtpack tool, the following section can get more clearly description.

### 12.1 Linux version nvtpack for all-in-one image

The nvt-nvtpack.dtsi is used to control what kinds of images want to be involved, and which files will be packed by all-in-one tool. If source\_file = "", it means we don’t want to pack this image into all-in-one image. If id1 … source\_file = "nvt-evb.bin", it means nvt-evb.bin file will pack into all-in-one image partition 1, partition setting we can reference nvt-storage-partition.dtsi file.

nvtpack {

???? ver = "NVTPACK\_FW\_INI_16072017"; /* Fixed */

???? method = &lt;1&gt;; /* Fixed */

???? index {

????????????? id0 { partition\_name = "loader";????? source\_file = ""; }; /* Fixed */

????????????? id1 { partition\_name = "fdt";???????? source\_file = "nvt-all.bin"; }; /* Fixed */

????????????? id2 { partition\_name = "fdt.restore"; source\_file = "";???? }; /* Fixed */

????????????? id3 { partition\_name = "atf";???????? source\_file = "atf.bin"; };

????????????? id4 { partition\_name = "uboot";??? ????? source\_file = "u-boot.bin"; };

????????????? id5 { partition\_name = "uenv";???? ????? source\_file = ""; };

????????????? id6 { partition\_name = "kernel";????? source\_file = "Image.bin"; };

????????????? id7 { partition\_name = "rootfs";????? source\_file = "rootfs.ramdisk.bin"; };

????????????? id8 { partition\_name = "rootfs1";???? source\_file = "rootfs_1.rw.ubifs.bin"; };

???? };

};

??????? Using “make all” or “make pack” can generate the packed image is under output/packed/FW(SOC).bin.

### 12.2 Update Firmware

Insert SD card including All-in-One bin to the target board and power on can update firmware.

### 12.3 Update Loader

For a blank Nand flash, you need to burn loader (LD98336A.bin), by first SD card format (be sure to format), and then immediately put LD98336A.bin, then placed all in one bin (FW98336A.bin).

  

13 Power on
-----------

### 13.1 How to power on

To follow update steps to burn the desired Image, remove SD card can boot up directly.

  

14 Debug
--------

The following list provides comparison and classification of the debugging tools.

|     |     |     |
| --- | --- | --- |
| Name | Classification | Description |
| Coredump | AP debug | Generated file for the further analysis when the program has terminated abnormally |
| Messages | AP/Kernel debug | To record Linux kernel and AP booting log |
| GDB | AP debug | To debug target board application from remote server |
| printk | Kernel debug | Basic kernel/module debug usage |
| kmemleak | Kernel debug | To analyze if Linux kernel has memory leak issue. |
| OPENOCD | Kernel debug | To debug/ trace kernel or uboot |

### 14.1 Coredump

Provide analytical application error log, the application does not properly terminated, it generates a file in /var/log. It can record the program name, PID and time, can be loaded for analysis through a cross compiler. You should build it with debug mode when you start application analysis.

The following is related setting:

$ cd na51090\_linux\_sdk/root-fs/rootfs/

$ vi etc/profile

\# coredump setting

echo 1 > /proc/sys/kernel/core\_uses\_pid

ulimit -c unlimited

echo "/var/log/core-%e-%p-%t" > /proc/sys/kernel/core_pattern

  

### 14.2 Messages

The boot log of the Linux will be stored in /var/log/messages, this file can involve Kernel and user space app. If the kernel crash occurred, please provide this file for the further analysis.

### 14.3 GDB

GDB (GNU Project Debugger) can support Remote and Target mode to debug AP.

Target mode gdb/gdbserver can be generated by the following command:

$ cd na51090\_linux\_sdk/tools

$ make gdb

The connection diagram as shown below, Figure 13-1:

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image018.png)

Figure 14-1 Target debug connection

Remote mode can debug user space application through GDB server, and the connection architecture as below. Linux server is x86_64 compile server, target board is the EVB, they can be connected by serial or TCP/IP. Linux server will use cross compiler toolchain GDB to debug target board AP, this AP must be enabled debug symbol, and target board also needs to execute gdbserver which can be find in toolchain.

The serial connection can connect USB-to-Serial cable to target board USB port, and check if there is /dev/ttyUSB0 existed.

TCP/IP connection can use Wi-Fi or Ethernet, install necessary drivers and confirm whether it can ping to server.

![](NT9833x_SDK_Pure_Linux_Programming_Guide_en.files/image019.png)

Figure 14-2 Remote debug connection

GDB server needs to be executed on EVB.

$ cp tools/__install/bin/gdbserver root-fs/rootfs/bin/

$ cp tools/__install/bin/gdb root-fs/rootfs/bin/

And then, running below procedures can debug your AP.

1. Target Board

target > gdbserver comm prog \[args...\]

The gdbserver doesn’t loading debug symbol, all of the symbols will be loaded by the Linux server cross compiler gdb. It can reduce memory space in this way.

Serial:

target > gdbserver /dev/ttyUSB0 hello_world

Net:

target > gdbserver Host \_IP:1234 hello\_world

2. Linux Server

Serial:

Server > {CROSS_COMPILE}-gdb hello_world

Server > set remotebaud 115200

Server > target remote /dev/ttyUSB0

Net:

Server > {CROSS_COMPILE}-gdb hello_world

Server > target remote localhost:1234

Reference to below link can show you how to use command debug your AP: [http://sourceware.org/gdb/current/onlinedocs/gdb/index.html](http://sourceware.org/gdb/current/onlinedocs/gdb/index.html)

In addition to command mode debug you also can use DDD, it is a framework on top of GDB debug visualization software, you can install and use by below command:

$ sudo apt-get install ddd

$ sudo ddd --debugger aarch64-ca53-linux-uclibc-gdb

### 14.4 Printk

Linux provides seven levels of Log printk available in the following table:

|     |     |     |
| --- | --- | --- |
| **Level** | **Description** | **Usage** |
| (0) KERN_EMERG | system is unusable | pr_emerg |
| (1) KERN_ALERT | action must be taken immediately | pr_alert |
| (2) KERN_CRIT | critical conditions | pr_crit |
| (3) KERN_ERR | error conditions | pr_err |
| (4) KERN_WARNING | warning conditions | pr_warning |
| (5) KERN_NOTICE | normal but significant condition | pr_notice |
| (6) KERN_INFO | Informational | pr_info |
| (7) KERN_DEBUG | debug-level messages | pr_debug |

Above the printk level is used to decide whether or not to print the message console, the below instruction can show you the printk level, current representative of the level of the boot to be printed, default is the default level, minimum is the lowest possible print level, boot-time-default is boot stage log:

root@NVTEVM:~$ cat /proc/sys/kernel/printk

??????????????????????????????????????? 7?????? 4?????? 1?????? 7

current??? default??? minimum??????? boot-time-default

Kernel will compare the printed message log level, if the value is less than the current will be printed out. Therefore, to change the output level so that all messages are printed out can use this command:Kernel hui qu b?jiao yin ch? xunxi de log level, rugu? xi?oyu current de zhi jiu hui yin ch?lai.  
Y?nc?, yao g?ibian sh?ch? jibie rang su?y?u xunxi d?u k?y? yin ch?lai k?y? yong d?xia f?ngshi:您是不是要查：  Linux除了_Built_-in的Driver之外,還有提供外部載入的方式稱之為Kernel module,可透過insmod或是modprobe做載入,底下分為build-in module與out-of-tree module做編譯介紹。

root@NVTEVM:~$ echo 8 > /proc/sys/kernel/printk

### 14.5 Kmemleak

Linux Kmemleak is provided for detecting a memory leak tool, it will record detect report in /sys/kernel/debug/kmemleak, to use this function as long as enable the "Kernel Hacking", "Kernel Memory Leak Detector" (CONFIG\_DEBUG\_KMEMLEAK) in the kernel option, and configure the "Maximum kmemleak early log entires" with 1200.

Clear current record:

root@NVTEVM:~$ echo clear > /sys/kernel/debug/kmemleak

Testing your driver:

root@NVTEVM:~$ insert YourModule.ko

Scan:

root@NVTEVM:~$ echo scan > /sys/kernel/debug/kmemleak

Check the resules:

root@NVTEVM:~$ cat /sys/kernel/debug/kmemleak

  

15 FAQ
------

This section will list frequently problems.

### 15.1 Toolchain can’t be found

We have two toolchains to build overall SDK, one is for itron, another is for Linux.

First, please use below command to check your environment setting.

$ get\_stuff\_for_environment

### 15.2  Operation not permitted

The SDK installation path should be under your home folder, you should use the same owner to decompressing and building, otherwise you will get “_operation not permitted_” related message.

Please use below command to check permission and owner.

$ ls -al YOUR_FOLDER

### 15.3  Linux kernel uImage can’t be generated

This is because our default setting is lz4 compression format, you should follow section 1.2 to check lz4 tool is installed.

Try to use lz4 command to check your compiling environment.

$ lz4