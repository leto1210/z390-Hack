# Software

---
Setup for a Mac 19,2 with Clover 5033

Mojave version 10.14.6 for AMD Vega native support

* Jump to [Explain ACPI](./config_explain_ACPI.md)
* Jump to [Explain BOOT](./config_explain_BOOT.md)
* Jump to [Explain DEVICES](./config_explain_DEVICES.md)
* Jump to [Explain Kernel And Kext Patches](./config_explain_KandKexTPatches.md)
* Jump to [Explain SSDT USB](./config_ssdt_usb.md)


## Create macOS Installation

macOS Mojave version 10.14.5
* Format USB (minimum 8 GB) `diskutil eraseDisk JHFS+ USB /dev/disk#`
> The above command was required for a USB drive which did not have an EFI partition, not created with the GUID partition scheme. The option to create the GUID partition scheme was not in the Mojave Disk Utility GUI.
* Create a macOS USB installer `sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/USB`
* Install Clover to USB installer
* Run Clover Configurator to create/update EFI partition, or copy EFI folder here to the EFI partition

## Installing Clover

Using Clover version 5033

_Under UEFI Drivers (Recommanded / FileSystem / Memory Fix / Additional) choose:_
* _ApfsDriverLoader_ - This allows Clover to see and boot from APFS volumes by loading apfs.efi from ApfsContainer located on block device
*  _OsxAptioFix3Drv.efi_ - Fixing some UEFI APTIO Firmware issues relevant to booting macOS (As AptioMemoryFix is not working on my config)
* _EmuVariableUefi_ - Fix mvram not present on my Asus MB
* _FSInject_ 
* _HFSPlus_ - Apple official driver for HFS Plus

Check _Install RC scripts on target volume_ - Fix with EmuVariableUefi nvram problem with my Asus MB

## Config.plist

```markup
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>ACPI</key>
	<dict>
		<key>AutoMerge</key>
		<true/>
		<key>DSDT</key>
		<dict>
			<key>Fixes</key>
			<dict>
				<key>FixShutdown</key>
				<true/>
			</dict>
		</dict>
		<key>FixHeaders</key>
		<true/>
		<key>SSDT</key>
		<dict>
			<key>Generate</key>
			<dict>
				<key>PluginType</key>
				<true/>
			</dict>
		</dict>
	</dict>
	<key>Boot</key>
	<dict>
		<key>Arguments</key>
		<string>slide=0</string>
		<key>DefaultVolume</key>
		<string>LastBootedVolume</string>
		<key>NoEarlyProgress</key>
		<true/>
		<key>Timeout</key>
		<integer>8</integer>
		<key>XMPDetection</key>
		<string>Yes</string>
	</dict>
	<key>Devices</key>
	<dict>
		<key>Audio</key>
		<dict>
			<key>Inject</key>
			<integer>1</integer>
		</dict>
		<key>Properties</key>
		<dict>
			<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
			<dict>
				<key>AAPL,ig-platform-id</key>
				<data>
				AwCSPg==
				</data>
				<key>AAPL,slot-name</key>
				<string>Internal</string>
				<key>device_type</key>
				<string>VGA compatible controller</string>
				<key>hda-gfx</key>
				<string>onboard-1</string>
				<key>model</key>
				<string>UHD Graphics 630 (Desktop)</string>
			</dict>
		</dict>
	</dict>
	<key>GUI</key>
	<dict>
		<key>Hide</key>
		<array>
			<string>PreBoot</string>
			<string>Recovery</string>
			<string>Windows</string>
		</array>
		<key>Mouse</key>
		<dict>
			<key>Enabled</key>
			<true/>
			<key>Speed</key>
			<integer>8</integer>
		</dict>
		<key>Scan</key>
		<dict>
			<key>Entries</key>
			<true/>
			<key>Legacy</key>
			<false/>
			<key>Linux</key>
			<false/>
			<key>Tool</key>
			<true/>
		</dict>
		<key>Theme</key>
		<string>embedded</string>
	</dict>
	<key>KernelAndKextPatches</key>
	<dict>
		<key>AppleRTC</key>
		<true/>
	</dict>
	<key>RtVariables</key>
	<dict>
		<key>MLB</key>
		<string>C029128024NLNV98C</string>
		<key>ROM</key>
		<string>UseMacAddr0</string>
	</dict>
	<key>SMBIOS</key>
	<dict>
		<key>BiosReleaseDate</key>
		<string>04/22/2019</string>
		<key>BiosVendor</key>
		<string>Apple Inc.</string>
		<key>BiosVersion</key>
		<string>IM191.88Z.F000.B00.1904222222</string>
		<key>Board-ID</key>
		<string>Mac-63001698E7A34814</string>
		<key>BoardManufacturer</key>
		<string>Apple Inc.</string>
		<key>BoardSerialNumber</key>
		<string>C02927207GUKGQGUE</string>
		<key>BoardType</key>
		<integer>10</integer>
		<key>BoardVersion</key>
		<string>1.0</string>
		<key>ChassisAssetTag</key>
		<string>iMac-Aluminum</string>
		<key>ChassisManufacturer</key>
		<string>Apple Inc.</string>
		<key>ChassisType</key>
		<string>0x09</string>
		<key>EfiVersion</key>
		<string>220.260.170.0.0</string>
		<key>Family</key>
		<string>iMac</string>
		<key>FirmwareFeatures</key>
		<string>0xFD8FF576</string>
		<key>FirmwareFeaturesMask</key>
		<string>0xFF1FFF3F</string>
		<key>LocationInChassis</key>
		<string>Part Component</string>
		<key>Manufacturer</key>
		<string>Apple Inc.</string>
		<key>Mobile</key>
		<false/>
		<key>PlatformFeature</key>
		<string>0x00</string>
		<key>ProductName</key>
		<string>iMac19,2</string>
		<key>SerialNumber</key>
		<string>XXXXXXXXXXXXXXXXX</string>
		<key>SmUUID</key>
		<string>XXXXXXXXXXXXXXXXX</string>
		<key>Version</key>
		<string>1.0</string>
	</dict>
	<key>SystemParameters</key>
	<dict>
		<key>InjectSystemID</key>
		<true/>
	</dict>
</dict>
</plist>
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
