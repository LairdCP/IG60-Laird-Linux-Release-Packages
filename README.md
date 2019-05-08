# IG60-Laird-Linux-Release-Packages
IG60 Development Kit and Source Releases.  For source release instructions and a getting started guide, jump to the introduction. For binary development kit images and a prebuilt SDK, see the releases page linked below. Source releases require binaries from the development kit binary releases.  For these binaries and the development kit binary images, also see the link below:

<https://github.com/LairdCP/IG60-Laird-Linux-Release-Packages/releases>

# Introduction
## Purpose
The reference guide is intended to provide an embedded developer with the information needed to start evaluating and integrating the Sentrius™ IG60 gateway using Laird Linux for their IoT connectivity and processing needs.  The guide is designed to walk the developer integrating the IG60 Laird Linux gateway through the same process Laird developers use to develop our own boxed products. This allows multiple levels of Laird's customer support team to assist with customer integrations.
## Product Overview
The Sentrius™ IG60 using Laird Linux has a small footprint for easy installation and a rugged, industry spec design that enables it to withstand wide temperature ranges, humidity, shock, and vibration. Certified for industry environment, the IG60 is ideal for industry deployment.

The IG60 can use several wired and wireless interfaces, collecting data and using customer applications on top of Laird Linux to process and send data to a variety of cloud solutions.

The IG60 comes standard with IEEE 802.11ac 2x2, Bluetooth 4.2, Ethernet, USB, SD and serial interfaces.

Example customer use cases that can be developed using the IG60 running Laird Linux:
* Remotely monitor and control your infrastructure and surveillance equipment on pipelines, meters, pumps and valves in any energy, utility or industrial application.
* Instantly connect your equipment at remote locations or temporary sites.
* Providing reliable internet connectivity to remote workers.
* Connecting your machines to IoT platform (Such as Microsoft Azure, Amazon AWS, and PTC ThingWorx, etc.) for continuous monitoring and visualization.
# Hardware Information
## Gateway Interfaces
![Gateway Connectors](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_connectors.png?raw=true)
## Power Supply
The IG60 supports a voltage range between 9 V and 36V. The following figure shows the power connector on the IG60.The IG60 comes with a 12V/2.5A AC power adapter. 
![Power Port](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_power_port.png?raw=true)
![Power Port Pin Out](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_power_port_pin_out.png?raw=true)
An optional DC power cable with three meter length is available for the IG60, as shown below.
![Power Cord](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_power_cord.png?raw=true)
## Wired Interfaces

### Serial Ports
The serial port supports RS232, RS422 and RS485 modes via a D-Sub9 connector. The IG60 can then take that information and re-encode it in a format such as MQTT, preparing it for an IoT platform like AWS.
* Complies with the EIA RS-232, RS-422, and RS-485 specification.
* Supports up to 115.2 kbps baud rate.
* Software selectable RS-232/422/485 communication.
* Output driver levels swing from -7 VDC to +7 VDC with normal loading.
* Input voltage ranges from -25 VDC to +25 VDC.
* The following table provides the pin definition of the D-Sub9 connector for various operation modes.

The following table summarizes the serial pins in their various specifications and duplex settings.
![Serial Port](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_serial_port.png?raw=true)
![Serial Pin Out](https://github.com/LairdCP/content_imgs/blob/master/ig60/ig60_power_port_pin_out.png?raw=true)
### Ethernet
There are two ethernet ports on the IG60.
* LAN1 for 10/100 Mbit/s
* LAN2 for 10/100/1000 Mbit/s
For to indication Ethernet status, there are two embedded LEDs are associated with each port.
### USB 
The USB-A connector on the IG60 supports connection to USB devices. The USB device port supports the USB 2.0 standard, at high speed, full speed, and low speed data rates.
### Antenna Ports
There are two SMA antenna ports on the IG60, for WLAN1 and WLAN2. These two connectors are fitted with the two included dipole antennas

## Wireless Interfaces
### Wi-Fi
The gateway's 802.11ac Wi-Fi features 2x2 MU-MIMO support, powered by the Marvell 88W8997 chipset. Additional spatial streams provide higher wireless throughput, and a dedicated cryptographic chip provides FIPS 140-2 encryption for sensitive data.

The Wi-Fi connection is supported by both the WLAN1 and WLAN2 antennas.
### Bluetooth
With Bluetooth 5, the gateway provides both Classic Bluetooth and Bluetooth Low Energy connection. Bluetooth Low Energy is ideal for collecting intermittent sensor data from a large number of sources, while Classic Bluetooth can accept virtual serial port or other higher bandwidth data streams.

The Bluetooth connection is supported by the WLAN2 antenna.
### Data Storage
#### Onboard Flash Memory
The IG60 features 512 MB of internal NAND Flash memory available for your customized image of Laird Linux with your applications.
#### MicroSD Slot
The MicroSD slot (SDHC, SD Card 2.0) provides a large amount of removable storage. For initial bring up, the SD card development kit images are the first use of the MicroSD slot. In a production environment, this slot is especially useful for instances where large amounts of data need to be logged or preserved. For example, for instances where wireless signal is temporarily lost, data can be backed up via a micro SD slot and sent to its destination when connection is re-established. The MicroSD slot provides potentially hundreds of gigabytes of data storage for your applications.
## Using the Debug Console
For the SD card images, the Serial Port is a debug console. Connect a serial cable cable from your computer to the Serial Port on the IG60. During development and evaluation, a serial console program is required.  Laird recommends the use of minicom on Linux or PuTTY on Windows. If using the recommended Ubuntu operating system for evaluation or development, you can install minicom as follows:

* `$ sudo apt install minicom`

Once the Serial Port on the IG60 is connected to your Ubuntu computer, you should have a new /dev/ttyUSB device that has enumerated. Assuming this enumeration is /dev/ttyUSB0, the console of the IG60 can be accessed with minicom via the following command:

* `$ sudo TERM=linux minicom -o -D /dev/ttyUSB0`

If you power cycle the IG60, you should see a boot-up sequence similar to below. The example boot output has been heavily truncated to fit in this guide.

```
RomBOOT

U-Boot SPL 2018.01-ig60sd (Jan 31 2019 - 12:56:52)
Trying to boot from MMC0
reading u-boot.itb

U-Boot 2018.01-ig60sd (Jan 31 2019 - 12:56:52 -0500)

CPU: SAMA5D36
Crystal frequency:       12 MHz
CPU clock        :      528 MHz
...
Hit any key to stop autoboot:  0
reading kernel.itb
4360555 bytes read in 282 ms (14.7 MiB/s)
## Loading kernel from FIT Image at 21000000 ...
...
## Loading loadables from FIT Image at 21000000 ...
   Trying 'script@1' loadables subimage

   Verifying Hash Integrity ... sha256+ OK
   Loading Kernel Image ... OK
   Loading Device Tree to 27732000, end 2773e0a3 ... OK

Starting kernel ...

...

Welcome to Laird Linux development build 20190131!

[  OK  ] Created slice system-serial\x2dgetty.slice.
...
[  OK  ] Started Hostname Service.

Laird Linux development build 20190131
summit login:
```
## Login and Example WiFi Scan
Once you see `summit login:`, you are at the end of booting and can login using the user "root" and the password "summit". Once logged in, you can query for a basic WiFi scan list to see available networks using the command below:

```
# nmcli dev wifi list
IN-USE  SSID         MODE   CHAN  RATE        SIGNAL  BARS  SECURITY         
        --           Infra  149   270 Mbit/s  35      **    WPA2             
        NowYouSeeMe  Infra  153   270 Mbit/s  30      *     WPA2             
        wfa19        Infra  149   405 Mbit/s  29      *     WPA2 802.1X      
        wfa9ac       Infra  149   405 Mbit/s  27      *     WPA2             
        wfa0ac       Infra  149   405 Mbit/s  27      *     --               
        wfa18        Infra  149   405 Mbit/s  25      *     WPA1 WPA2 802.1X 
        wfa20        Infra  149   405 Mbit/s  25      *     WPA1 WPA2 802.1X 
        nps_aes      Infra  149   405 Mbit/s  25      *     WPA2 802.1X      
        11w_psk      Infra  149   405 Mbit/s  25      *     WPA2             
        11w_dot1x    Infra  149   405 Mbit/s  25      *     WPA2             
        wfa21        Infra  149   405 Mbit/s  25      *     WPA1 WPA2
```
For network configuration examples, please see the [NetworkManager](#networkmanager) section.
# Software Information
## Prerequisites
### Linux Development Environment Setup
These are Laird's recommendation for setting up a development environment for use with Laird's Buildroot based Linux board support package.
#### Ubuntu
Laird recommends Ubuntu 16.04 as the base operating system for your development. All instructions in this reference guide assume a developer on an Ubuntu 16.04 system.
#### SSH
Laird makes extensive use of GitHub and having proper Secure Shell (SSH) access to our repositories on GitHub. If you haven't set up SSH, you can use the instructions below to enable SSH for use with GitHub.
1. Check whether your private key (~/.ssh/id_rsa) and public key (~/.ssh/id_rsa.pub) files exist
  1. `$ ls -1 ~/.ssh/id_rsa*`
2. If they do not, generate them
  1. `$ ssh-keygen`
    1. Accept default file paths
    2. Accept no passphrase
3. View your public key
  1. `$ cat ~/.ssh/id_rsa.pub`

#### git
Laird delivers the Laird Linux board support package using git repositories. If you haven't set up git, you can use the instructions below to enable git for use with GitHub.
* Install and configure the "git" package
  1. `$ sudo apt install git`
  2. `$ git config --global user.name "John Doe"`
  3. `$ git config --global user.email "john.doe@yourcompany.com"`
  4. `$ git config --list`
    1. Expect user.name=John Doe
    2. Expect user.email=john.doe@yourcompany.com

#### repo
Laird uses the repo tool from the Android project to pull down and correctly layout the git repositories that comprise the Laird Linux board support package. To install repo on Ubuntu, use the instructions below.
* `$ sudo apt install repo`

You can also get it by following the instructions here:
* (https://source.android.com/source/downloading.html#installing-repo)

#### Github Account
Laird Linux board support packages are availabe on GitHub. The most seamless workflow throughout a integration is to set up a GitHub account (https://github.com/) and add your SSH public key to your GitHub account. Instructions for setting up a GitHub account and adding an SSH key are below.
1. Go to (https://github.com/join) and follow the instructions.
2. Once you have a GitHub account add your public SSH key generated previously.
  1. View your public key
    1. `$ cat ~/.ssh/id_rsa.pub`
  2. This should be similar to:
    1. `ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDW5HxCJe56MZKkGxtHU2hkb1uyuJ3i+AFZNnSIApiDe1l1H9Y40YjBF+sE47GKgNuzQIMqKZ6xjRdb8KxvtjQIE/VcSiz9KIaFtKce/wKKxy0vOXbskSLzELlA9ovY9AJmp3qUaW+BEChnggERjPvq+1oyiKGRJzo51j/CQr+Yx8c2MtKubjHknKkQ2Th8kxL1bQj4lVgyfqNGj3DXUz9S+kTm+dLnmmOXlUfxx8Khrb7j0Dg+lk1lqeolqt6aFwpMnb8V2h5lDevJ0YSSyId01OnaAnIlx1lc+zauctsgtZf5Htl9cXS7Cp3OCMfSa+IKFeFL9/ku9C25EdA5zOnt your@email.com`
  3. Copy the contents of the above output to you clipboard
  4. Follow the instructions at
	 (https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/) starting with Step 2.

## Laird Linux
### Overview
Laird Linux is Laird's board support package specifically tailored for Laird's gateways and customer's connectivity driven use cases. Laird regularly updates Laird Linux by merging in the upstream Linux kernel and Buildroot. We merge in major long-term support kernel releases which allow our gateways to utilize the latest in drivers and kernel space functionality, performance enhancements, security, and bug fixes.  Also, we merge in major long-term support Buildroot releases which provide for the latest in over 2200 user space applications and libraries. Laird Linux takes this solid upstream heritage and integrates our custom platform enhancements for connectivity, security, and power consumption.

### Buildroot
The core piece of Laird Linux is [Buildroot](https://buildroot.org/). Buildroot is a from source build system designed to allow the customer to create a customized Linux image for a target embedded computing module. Buildroot is capable of configuring and building the bootloader, kernel, and rootfs for Laird's gateways. Buildroot's core build system technologies are the well-known and easy to understand [make](https://en.wikipedia.org/wiki/Make_(software)) build tool and [kconfig](https://www.kernel.org/doc/Documentation/kbuild/kconfig-language.txt) configuration tool. This enables easy build customization through the user interface tools [menuconfig](https://en.wikipedia.org/wiki/Menuconfig) or xconfig and Buildroot make commands. The [Linux kernel](https://www.kernel.org/), [U-Boot bootloader](http://www.denx.de/wiki/U-Boot/WebHome), and [Busybox core userspace ulilities toolkit](https://en.wikipedia.org/wiki/BusyBox) all use make, Kconfig, and menuconfig. Build and configuration concepts found in one translate nicely to another. Buildroot has easy to read and extensive documentation available at (https://buildroot.org/docs.html) in pdf, html, and ascii form.  If time permits, Laird highly recommends following the Training section of the documentation landing page.

Laird's Buildroot is a fork of the upstream [Buildroot stable](https://git.busybox.net/buildroot/). Starting with and merging upstream allows Laird to know the authenticity of Buildroot's source code and better verify the security of our fork. Laird targets [long-term support releases (LTS)](https://buildroot.org/download.html) for merging into our Buildroot fork.

### Linux Kernel
Laird's kernel is a fork the upstream [Linux stable kernel](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/). Starting with and merging upstream allows Laird to know the authenticity of the kernel's source code and better verify the security of our fork. Laird targets [long-term support releases (LTS)](https://www.kernel.org/category/releases.html) for merging into our kernel fork.

### Toolchain
Laird preselects prebuilt toolchains for each release of Laird Linux for our gateways. The advantage of using a preselected and prebuilt toolchain is the high level of QA verification on common components between stock Laird development images and customer images. We are currently ultilizing prebuilt toolchains from [Bootlin’s toolchain program](https://toolchains.bootlin.com).  Bootlin, who is major contributor to Buildroot, provides a variety of prebuilt toolchains created from Buildroot's toolchain building capabilties. Laird selects toolchains that have been marked stable by the Buildroot community and use proven components. Beyond the toolchains themselves, Bootlin also stores the following artifacts for reference from their Buildroot based toolchain generation process: README of all essential information, defconfig fragment to generate toolchain, build log, software bill-of-material (SBOM), test system image, and test system defconfig. Laird configures each Laird Linux release to automatically download and use the correct toolchain.

### Versioning
Laird Linux releases follow an A.B.C.D versioning scheme. Rolling the A.x.x.x digit indicates we have merged a new major LTS kernel version and created a new git branch. Once we merge the new LTS kernel, B.C.D go to A.0.0.0. For example the 6.0.0.x releases are based on the 4.14.x LTS kernel and the 7.0.0.x releases are based on the 4.19.x LTS kernel. All new A.0.0.x releases also merge the latest LTS Buildroot. For example the 6.0.0.x releases are based on the 2018.02.x LTS Buildroot and the 7.0.0.x releases are based on the 2019.02.x LTS Buildroot. Laird rolls the x.B.x.x digit to indicate that a new major LTS Buildroot has been merged on a specific A.x.x.x LTS kernel after its initial Buildroot release. The x.x.C.x digit is reserved for future use. The x.x.x.D digit indicates the build number for that A.B.C.x release.

### Release Types
Laird Linux has two branch and release types. Every A.0.0.x branch of Laird Linux will have at minimum two releases, one release (R1) in Q2 and another (R2) in Q4 of the first year it is released. These will be pushed to our public Github site. Certain Laird Linux branches will be declared long-term support branches. These long-term support branches will consist of 5 scheduled releases and an extended support period for 5 years after the first 5 scheduled releases. The LTS branches will have the normal Q2 (R1) and Q4 (R2) releases in their first calendar year, a Q2 (R3) and Q4 (R4) sustaining release in their second calendar year, a Q2 (R5) sustaining release in their third calendar year, and 5 additional years of extended support releases as needed. This will allow for 7 years of support on a LTS branch. If you're interested in using the R3, R4, R5, or extended support releases of a LTS branch, please contact your Laird sales representative for more details and pricing.

## Getting started with a Developer's SD Card Image and a SDK
This section will walk a developer through following:

* [Downloading a developer's SD card image](#downloading-a-developers-sd-card-image)
* [Flashing a developer's SD card image](#flashing-a-developers-sd-card-image)
* [Using a prebuilt SDK](#using-a-prebuilt-sdk)
* [Downloading the board support package source code](#downloading-the-board-support-package-source-code)
* [Building the developer's SD card image](#building-the-sd-card-developers-image)
* [Creating a custom SDK](#create-a-custom-sdk)

### Downloading a developer's SD card image
Laird Linux releases include a prebuilt SD card image as a starting point for evaluating and integrating a Laird Linux release on a Laird gateway. For the IG60, these prebuilt images are found on at [IG60 Laird Linux release page](https://github.com/LairdCP/IG60-Laird-Linux-Release-Packages/releases). These releases are named ig60sd-laird-A.B.C.D.tar.bz2. These prebuilt SD card images are good for quickly testing a IG running the latest software.

### Flashing a developer's SD card image
Once the image is downloaded. Extract the image:
```
~/Downloads/ig60sd$ tar -xvf ig60sd-laird-7.0.0.38.tar.bz2 
ig60sd-laird-7.0.0.38/
ig60sd-laird-7.0.0.38/ig60sd-target-sbom-20190222
ig60sd-laird-7.0.0.38/ig60sd-host-sbom-20190222
ig60sd-laird-7.0.0.38/u-boot-spl.bin
ig60sd-laird-7.0.0.38/u-boot.itb
ig60sd-laird-7.0.0.38/rootfs.tar
ig60sd-laird-7.0.0.38/ig60sd-sdk.tar.bz2
ig60sd-laird-7.0.0.38/legal-info-20190222.tar.bz2
ig60sd-laird-7.0.0.38/kernel.itb
ig60sd-laird-7.0.0.38/mksdcard.sh
ig60sd-laird-7.0.0.38/mksdimg.sh

```
To flash the image to an SD card use the mksdcard.sh script. The mksdcard.sh script takes the target device as an argument and will ask if you'd like to proceed with removing all data on your SD card and flashing a new image.  This is shown below:
```
~/Downloads/ig60sd-laird-7.0.0.34$ sudo ./mksdcard.sh /dev/sdc
[sudo] password for user: 
*************************************************************************
WARNING: All data on /dev/sdc now will be destroyed! Continue? [y/n]
*************************************************************************
[Partitioning /dev/sdc...]
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.653846 s, 1.6 MB/s
DISK SIZE - 1967128576 bytes
Checking that no-one is using this disk right now ... OK

Disk /dev/sdc: 1.9 GiB, 1967128576 bytes, 3842048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

>>> Created a new DOS disklabel with disk identifier 0x59c337f4.
Created a new partition 1 of type 'W95 FAT16 (LBA)' and of size 48 MiB.
/dev/sdc2: Created a new partition 2 of type 'Linux' and of size 1.8 GiB.
/dev/sdc3: 
New situation:

Device     Boot  Start     End Sectors  Size Id Type
/dev/sdc1  *      2048  100351   98304   48M  e W95 FAT16 (LBA)
/dev/sdc2       100352 3842047 3741696  1.8G 83 Linux

The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
[Making filesystems...]
[Copying files...]
[Done]
```
You can now insert your SD card into the IG hardware development kit and press the reset button to boot into the new SD card image.

### Using a prebuilt SDK

Laird Linux releases include a prebuilt SDK to start doing application development for a Laird IG. For the IG60, this prebuilt SDK is called ig60sd-sdk-A.B.C.D.tar.bz2 and can be found with each release at the [IG60 Laird Linux release page](https://github.com/LairdCP/IG60-Laird-Linux-Release-Packages/releases). The prebuilt SDK includes the toolchain and all development files of the software packages used to generate the prebuilt SD card image from that release. The SDK can be set up for use with an IDE to allow application developers to not need a full BSP on their system. To use the SDK, extract the SDK tarball then run the script relocate-sdk.sh (located at the top directory of the SDK), to make sure all paths are updated with the new location. For more information on using SDKs generated from Laird's Buildroot fork, see the [Buildroot manual's section on the SDK](https://buildroot.org/downloads/manual/manual.html#_advanced_usage).

### Downloading the board support package source code

First step, pick which release you want. Odds are you want the most recent of your release.

Next, use repo to initalize and fetch your release. This is a two-step process: first you tell repo which manifest to use and then you tell it to fetch everything.

    mkdir ig60_6.0.0.132_source
    cd ig60_6.0.0.132_source
    repo init -u git@github.com:LairdCP/IG60-Laird-Linux-Release-Packages.git -m ig60_6.0.0.132.xml
    repo sync

_Note: Repo will initialize a .repo directory and then place all files directly in the directory that you are in when you run the `repo` command. So we recommend making a subdirectory and working in there._

#### Buildroot cache
In order to speed up builds, set up a Buildroot cache to store sources that Buildroot will download. Off your home directory:

    mkdir ~/.br2_dl_dir

Then add it to your build environment:

    export BR2_DL_DIR="${HOME}/.br2_dl_dir"

### Building the SD Card developer's image
Once your repo sync is finished, you are ready to build your own SD card image. This can be achieved by the following:

    cd wb
    make ig60sd

Once your build completes, you will find the output similar to below:
```
~/git/lrd-7.0.0.x/wb$ cd buildroot/output/ig60sd/images/
~/git/lrd-7.0.0.x/wb/buildroot/output/ig60sd/images$ ls -al
ig60sd-target-sbom-20190222
ig60sd-host-sbom-20190222
u-boot-spl.bin
u-boot.itb
rootfs.tar
ig60sd-sdk.tar.bz2
legal-info-20190222.tar.bz2
kernel.itb
mksdcard.sh
mksdimg.sh

```
You can see that the SD card image and the mksdcard.sh script are included.

### Create a custom SDK
If you'd like to create a custom SDK from your customized source build, while in the target's output directory, issue a `make sdk`:
```
~/git/lrd-7.0.0.x/wb/buildroot/output/ig60sd$ make sdk
```

## NetworkManager
Laird uses its own customized fork of NetworkManager for networking configuration, including WiFi profile management. For more information on using NetworkManager please see our [Laird NetworkManager User Guide](https://github.com/LairdCP/SOM60-Release-Packages/releases/download/LRD-REL-6.0.0.138/user_guide_laird_networkmanager_0.1.pdf).
