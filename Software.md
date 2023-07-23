# Software

---
Setup for a iMac 19,1 with OpenCore v093

Ventura version 13.4 with AMD RDNA2 native support

* Jump to [Explain ACPI](./config_explain_ACPI.md)
* Jump to [Explain BOOT](./config_explain_BOOT.md)
* Jump to [Explain DEVICES](./config_explain_DEVICES.md)
* Jump to [Explain SSDT USB](./config_ssdt_usb.md)


## Create macOS Installation

macOS Ventura version 13.4
* Format USB (minimum 16 GB) `diskutil eraseDisk JHFS+ USB /dev/disk#`
> The above command was required for a USB drive which did not have an EFI partition, not created with the GUID partition scheme. The option to create the GUID partition scheme was not in the Mojave Disk Utility GUI.

* Create a macOS USB installer `sudo /Applications/Install\ macOS\ Ventura.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
* Install OpenCore to USB installer
* Copy EFI folder here to the EFI partition

## Installing OpenCore

Using OpenCore version 093

_Under Drivers (Recommanded / FileSystem / Memory Fix / Additional) choose:_

* _OpenHFSPlus.efi_ - Apple official driver for HFS Plus
* _OpenRuntime.efi_ - Required
* _OpenCanopy.efi_ - Optional
* _ResetNvramEntry.efi_ - Required
* _ToggleSipEntry.efi_ - Optional


## Config.plist

```markup


```

## OpenCore Files

Kext | Usage
--- | ---
AppleALC.kext | Audio
VirtualSMC.kext | Required
SMCProcessor.kext | Metrics
SMCSuperIO.kext | Metrics
IntelMausi.kext | Ethernet
Lilu.kext | Audio + Graphics
WhateverGreen | Graphics
USBPorts.kext | USB [Codeless injection](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KEXTConcept/KEXTConceptAnatomy/kext_anatomy.html)
RadeonSensor.kext | Metrics [RadeonSensor project](https://github.com/aluveitie/RadeonSensor)
SMCRadeonGPU.kext | Metrics [RadeonSensor project](https://github.com/aluveitie/RadeonSensor)
