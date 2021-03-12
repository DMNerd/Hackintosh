# BigSur Hackintosh Asus Z390-p
My new Hackintosh repository for prime Z390-p Hackintosh. This was long time comming. This is not a full guide - it should serve as a outline/documentation of my build and insight as to why some thing are the way they are.

![SysInfo](https://github.com/DMNerd/Hackintosh/blob/main/Extra/Screenshots/Info.png)

## [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) 

Version: 0.6.7

OpenCanopy bootscreen is enabled and I am using the modern iconset

### Working:

As far as I can tell at this moment, this build is basically golden. Everything works as it should.

## Hardware 
| Part | Info/Link |
| --- | --- |
| **MoBo** | [ASUS PRIME Z390-P](https://www.asus.com/Motherboards-Components/Motherboards/All-series/PRIME-Z390-P/) |
| **CPU** | [i5 9600K Coffee Lake](https://ark.intel.com/content/www/us/en/ark/products/134896/intel-core-i5-9600k-processor-9m-cache-up-to-4-60-ghz.html) |
| **CPU Cooler** | Arctic Freezer 34 eSports, white|
| **iGPU** |  Intel UHD Graphics 630 |
| **dGPU** | Sapphire Radeon RX 460 4GB [bios modded](https://www.overclock.net/forum/67-amd/1633317-wip-rx460-rx560-conversion-pack-asus-gigabyte-msi-powercolor-sapphire-xfx.html "bios modded") to RX 560 4GB. Make sure your card is on the confirmed working if you feel like not risking it (this one is) |
| **RAM** | Patriot VIPER RGB 16GB (2x8GB) DDR4 3200 CL16, white|
| **Wifi/BT Card** | [Fenvi HB1200 PCI WiFi](https://www.aliexpress.com/item/33034394024.html?spm=a2g0s.9042311.0.0.69f64c4dVPLsGp) natively supported wifi card based on the BCM94360CS2 chipset |
| **Storage for MAC** | 128GB LiteOn NVMe SSD, 250GB Crucial Balistix SSD and 250GB Samsung 950 EVO + Seagate 1TB HDD and Seagate Barracuda 1TB HDD in raid 0|
| **Case** | [Fortron CMT240](https://www.fsp-europe.com/cmt240/) |
| **PSU** | [Be quiet! System Power 9 - 600W ](https://www.bequiet.com/en/powersupply/1279) |

## Native Power Management

![PM](https://github.com/DMNerd/Hackintosh/blob/main/Extra/Screenshots/pm.png)

## Kernel Extensions 

This setup is a bit more complicated. It uses all the same Kexts as my old setup coincidentally. But it needs couple of others to function properly.


**SMC:** [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases)

**Sound:** [AppleALC](https://github.com/acidanthera/applealc/releases) - the correct layout id for this setup is 5

**Graphics:** [Lilu](https://github.com/acidanthera/lilu/releases) and [WhateverGreen](https://github.com/acidanthera/whatevergreen/releases)

**LAN:** [RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X) 

**NVMeFix:** [NVMeFix](https://github.com/acidanthera/NVMeFix/releases/tag/1.0.5) - this one is needed for the NVMe slots on the moterboard (2 in total)

**RTCMemoryFixup:**[RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup/releases/tag/1.0.7) - this is needed to fix the RTC regions that cause the bios recovery issue. The blacklisted regions are: 58 and 59.

## USB Mapping

Here's the guide to how I decided to map the USB ports. This does not get over the 15 port limit.

![USBMap](https://github.com/DMNerd/Hackintosh/blob/main/Extra/Screenshots/usbmap.png)
