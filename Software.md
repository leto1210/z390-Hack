# Software

---
Setup for a iMacPro 1,1 with OpenCore v057

Catalina version 10.15.4 for AMD Vega native support

* Jump to [Explain ACPI](./config_explain_ACPI.md)
* Jump to [Explain BOOT](./config_explain_BOOT.md)
* Jump to [Explain DEVICES](./config_explain_DEVICES.md)
* Jump to [Explain Kernel And Kext Patches](./config_explain_KandKexTPatches.md)
* Jump to [Explain SSDT USB](./config_ssdt_usb.md)


## Create macOS Installation

macOS Mojave version 10.15.4
* Format USB (minimum 8 GB) `diskutil eraseDisk JHFS+ USB /dev/disk#`
> The above command was required for a USB drive which did not have an EFI partition, not created with the GUID partition scheme. The option to create the GUID partition scheme was not in the Mojave Disk Utility GUI.
* Create a macOS USB installer `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/USB`
* Install OpenCore to USB installer
* Copy EFI folder here to the EFI partition

## Installing Clover

Using OpenCore version 057

_Under Drivers (Recommanded / FileSystem / Memory Fix / Additional) choose:_
* _ApfsDriverLoader.efi_ - This allows OpenCore to see and boot from APFS volumes by loading apfs.efi from ApfsContainer located on block device
* _HFSPlus.efi_ - Apple official driver for HFS Plus
* _VirtualSmc.efi_ - Need for VirtualSMC Kexts
* _MemoryAllocation.efi_ - Required
* _OpenRuntime.efi_ - Required
* _OpenUsbKbDxe.efi_ -Required
* _VirtualSMC.efi_ - Required

## Config.plist

```markup



```

## OpenCore Files

Kext | Usage
--- | ---
AppleALC.kext | Audio
VirtualSMC.kext | Required
NVMeFix.kext | Enhanced compatibility
SMCLightSensor.kext | Metrics
SMCProcessor.kext | Metrics
SMCSuperIO.kext | Metrics
IntelMausi.kext | Ethernet
Lilu.kext | Audio + Graphics
WhateverGreen | Graphics
USBPorts.kext | USB [Codeless injection](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KEXTConcept/KEXTConceptAnatomy/kext_anatomy.html)
NoTouchID.kext | Disable TouchID call for authentification
