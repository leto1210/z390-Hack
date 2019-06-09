# Software

---
Setup for a Mac 19,1 with Clover 4945

Mojave version 10.14.5 for AMD Vega native support

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

Using Clover version 4945

_Under UEFI Drivers choose:_
* _ApfsDriverLoader-64_ - This allows Clover to see and boot from APFS volumes by loading apfs.efi from ApfsContainer located on block device
* _AptioMemoryFix-64_ - Fixing some UEFI APTIO Firmware issues relevant to booting macOS
* _EmuVariableUefi-64_ - Fix mvram not present on my Asus MB
* _FSInject-64_ 
* _HFSPlus_ - Apple official driver for HFS Plus

Check _Install RC scripts on target volume_ - Fix with EmuVariableUefi-64 nvram problem with my Asus MB

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
			<key>Patches</key>
			<array>
				<dict>
					<key>Comment</key>
					<string>change SAT0 to SATA</string>
					<key>Disabled</key>
					<false/>
					<key>Find</key>
					<data>
					U0FUMA==
					</data>
					<key>Replace</key>
					<data>
					U0FUQQ==
					</data>
				</dict>
			</array>
		</dict>
		<key>DropTables</key>
		<array>
			<dict>
				<key>Signature</key>
				<string>DMAR</string>
			</dict>
			<dict>
				<key>Signature</key>
				<string>MATS</string>
			</dict>
		</array>
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
		<string>keepsyms=1 dart=0 slide=0 debug=0x100 shikigva=40</string>
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
			<integer>7</integer>
		</dict>
		<key>USB</key>
		<dict>
			<key>Inject</key>
			<false/>
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
		<string>DarkBoot</string>
	</dict>
	<key>Graphics</key>
	<dict>
		<key>Inject</key>
		<dict>
			<key>Intel</key>
			<false/>
		</dict>
	</dict>
  <key>KernelAndKextPatches</key>
	<dict>
		<key>AppleIntelCPUPM</key>
		<true/>
		<key>AppleRTC</key>
		<true/>
	</dict>
	<key>RtVariables</key>
	<dict>
		<key>MLB</key>
		<string>xxxxxxxxx</string>
		<key>ROM</key>
		<string>UseMacAddr0</string>
	</dict>
	<key>SMBIOS</key>
	<dict>
		<key>BiosReleaseDate</key>
		<string>02/18/2019</string>
		<key>BiosVendor</key>
		<string>Apple Inc.</string>
		<key>BiosVersion</key>
		<string>IM191.88Z.F000.B00.1902181222</string>
		<key>Board-ID</key>
		<string>Mac-xxxxxxx</string>
		<key>BoardManufacturer</key>
		<string>Apple Inc.</string>
		<key>BoardSerialNumber</key>
		<string>xxxxxxxxxxx</string>
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
		<string>220.250.368.0.0</string>
		<key>Family</key>
		<string>iMac</string>
		<key>FirmwareFeatures</key>
		<string>0xFC0FE137</string>
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
		<string>iMac19,1</string>
		<key>SerialNumber</key>
		<string>xxxxxxxxx</string>
		<key>SmUUID</key>
		<string>xxxxxxxx</string>
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
