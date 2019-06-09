# Software

---
Setup for a Mac 19,1 with Clover 4945

Mojave version 10.14.5 for AMD Vega native support

## Create macOS Installation

macOS Mojave version 10.14.5
* Format USB (minimum 8 GB) `diskutil eraseDisk JHFS+ USB /dev/disk#`
> The above command was required for a USB drive which did not have an EFI partition, not created with the GUID partition scheme. The option to create the GUID partition scheme was not in the Mojave Disk Utility GUI.
* Create a macOS USB installer `sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/USB`
* Install Clover to USB installer
* Run Clover Configurator to create/update EFI partition, or copy EFI folder here to the EFI partition

## Installing Clover

Using Clover version 4945

_Under UEFI Drivers choose:_
* _ApfsDriverLoader-64_ - This allows Clover to see and boot from APFS volumes by loading apfs.efi from ApfsContainer located on block device
* _AptioMemoryFix-64_ - Fixing certain UEFI APTIO Firmware issues relevant to booting macOS
* _EmuVariableUefi-64_ - Fix mvram not present on my Asus MB
* _FSInject-64_ 
* _HFSPlus_ - Apple official driver for HFS Plus

Check _Install RC scripts on target volume_ - Fix with EmuVariableUefi-64 nvram problem with my Asus MB

## Config.plist

```markup
{r engine='bash', comment=''}
cat a.csv
```

## Clover Files

Kext | Usage
--- | ---
AppleALC.kext | Audio
VirtualSMC.kext | Required
SMCLightSensor.kext | Metrics
SMCProcessor.kext | Metrics
SMCBatteryManager.kext | Metrics
SMCSuperIO.kext | Metrics
IntelMausiEthernet.kext | Ethernet
Lilu.kext | Audio + Graphics
USBPorts.kext | USB [Codeless injection](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KEXTConcept/KEXTConceptAnatomy/kext_anatomy.html)
WhateverGreen.kext | Graphics
