# Ventura Hackintosh Asus Z390-p

My new Hackintosh repository for prime Z390-p Hackintosh. This was long time comming. This is not a full guide - it should serve as a outline/documentation of my build and insight as to why some thing are the way they are.

![SysInfo](https://github.com/DMNerd/Hackintosh/blob/main/Extra/Screenshots/Info.png)

## [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases)

Version: 0.9.1

OpenCanopy bootscreen is enabled and I am using the modern iconset. But Picker is set to function like the OG Apple picker and will only show up when holding apple keybinds.

### Working

As far as I can tell at this moment, this build is basically golden. Everything works as it should.

* Wifi/Bluetooth ✅
* File Vault ✅
* Apple Services ✅
  * iMessage  ✅
* Secure Boot ✅
* Hibernation in 'pmset -a hibernatemode 3' mode ✅
  * Sleep overall behaves like on real mac.
* Macos 13.3 Ventura ✅

## Hardware

| Part | Info/Link |
| --- | --- |
| **MoBo** | [ASUS PRIME Z390-P](https://www.asus.com/Motherboards-Components/Motherboards/All-series/PRIME-Z390-P/) |
| **CPU** | [i5 9600K Coffee Lake](https://ark.intel.com/content/www/us/en/ark/products/134896/intel-core-i5-9600k-processor-9m-cache-up-to-4-60-ghz.html) |
| **CPU Cooler** | Arctic Freezer 34 eSports, white|
| **iGPU** |  Intel UHD Graphics 630 |
| **dGPU** | AMD Radeon RX 5600 XT 6 GB |
| **RAM** | Patriot VIPER RGB 16GB (2x8GB) DDR4 3200 CL16, white|
| **Wifi/BT Card** | [Fenvi HB1200 PCI WiFi](https://www.aliexpress.com/item/33034394024.html?spm=a2g0s.9042311.0.0.69f64c4dVPLsGp) natively supported wifi card based on the BCM94360CS2 chipset. I replaced the stock antennas with stronger ones for better coverage |
| **Storage for MAC** | 128GB LiteOn NVMe SSD, 250GB Crucial Balistix SSD and Seagate Barracuda 1TB HDD |
| **Case** | [Fortron CMT240](https://www.fsp-europe.com/cmt240/) |
| **PSU** | [Be quiet! System Power 9 - 600W](https://www.bequiet.com/en/powersupply/1279) |

## Native Power Management

![PM] (<https://github.com/DMNerd/Hackintosh/blob/main/Extra/Screenshots/pm.png>)

## Kernel Extensions

This setup is a bit more complicated. It uses all the same Kexts as my old setup coincidentally. But it needs couple of others to function properly.

**SMC:** [VirtualSMC](<https://github.com/acidanthera/VirtualSMC/releases>)

**Sound:** [AppleALC](<https://github.com/acidanthera/applealc/releases>) - the correct layout id for this setup is 5

**Graphics:** [Lilu](<https://github.com/acidanthera/lilu/releases>) and [WhateverGreen](<https://github.com/acidanthera/whatevergreen/releases>)

**LAN:** [RealtekRTL8111](<https://github.com/Mieze/RTL8111_driver_for_OS_X>)

**NVMeFix:** [NVMeFix](<https://github.com/acidanthera/NVMeFix/releases>) - this one is needed for the NVMe slots on the moterboard (2 in total)

**HibernationFixup** [HibernationFixup](<https://github.com/acidanthera/HibernationFixup/releases>) - helps with hibernation

**RTCMemoryFixup:**[RTCMemoryFixup](<https://github.com/acidanthera/RTCMemoryFixup/releases/tag/1.0.7>) - this is needed to fix the RTC regions that cause the bios recovery issue. The blacklisted regions are: 58 and 59.

## USB Mapping

I use SSDT to map my ports for better future compatibility. It is also OS agnostic - it will only change usb properties on MacOS. You will have to create your own kext/ssdt if not using my exact MOBO.

| Count | Name | Type | Location |
|-------|------|------|----------|
| 1     | SS01 | 0x03 | Back     |
| 2     | SS02 | 0x03 | Back     |
| 3     | HS03 | 0x00 | Back     |
| 4     | HS04 | 0x00 | Back     |
| 5     | SS03 | 0x03 | Back     |
| 6     | SS04 | 0x03 | Back     |
| 7     | HS03 | 0x00 | Back     |
| 8     | HS04 | 0x00 | Back     |
| 9     | SS05 | 0x03 | Back     |
| 10    | SS06 | 0x03 | Back     |
| 11    | SS09 | 0x03 | Front    |
| 12    | SS10 | 0x03 | Front    |
| 13    | HS11 | 0x00 | Front    |
| 14    | HS12 | 0x00 | Front    |
| 15    | HS13 | 0xFF | Internal |

Others are unused/disabled
