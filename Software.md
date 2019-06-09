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
		<key>KernelPm</key>
		<false/>
		<key>KextsToPatch</key>
		<array>
			<dict>
				<key>Comment</key>
				<string>External icons patch</string>
				<key>Disabled</key>
				<true/>
				<key>Find</key>
				<data>
				RXh0ZXJuYWw=
				</data>
				<key>InfoPlistPatch</key>
				<false/>
				<key>MatchOS</key>
				<string>10.11.x,10.12.x,10.13.x,10.14.x</string>
				<key>Name</key>
				<string>com.apple.driver.AppleAHCIPort</string>
				<key>Replace</key>
				<data>
				SW50ZXJuYWw=
				</data>
			</dict>
		</array>
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

## SSDT (USB)

In this configuration, the 2 rear blue USB3.1 ports, USB 3.1 Gen2 Type C motherboard header, and USB 2.0 Hub headers are not enabled in order to stay within macOS's 15-port limit.

* Make sure `USBInjectAll.kext` and USB port limit patch is applied is applied
* Open About This Mac > System Report > Hardware > USB
* Take note of the USB 3.1 Bus PCI Device ID (0xa36d)
* Open SSDT-UIAC-ALL.dsl in MaciASL
* Find the section which matches the above PCI Device ID, and remove all other sections
* The current SSDT-UIAC file is configured as follows:
    * HS01: USB 3.1 Gen 2 rear - ENABLED
    * HS02: USB 3.1 Gen 2 rear - ENABLED
    * HS03: USB 3.1 Gen 2 rear - ENABLED
    * HS04: USB 3.1 Gen 2 rear connector (G31G2_C4) - ENABLED
    * HS05: USB 3.1 Gen 1 connector G31G2_C5 - DISABLED
    * HS06: connector USB_E12 - Asus Aura Lighting - DISABLED
    * HS07: USB 3.1 Gen 1 front - ENABLED
    * HS08: USB 3.1 Gen 1 front - ENABLED
    * HS09: USB 3.1 Gen 1 rear - DISABLED
    * HS10: USB 3.1 Gen 1 rear - DISABLED
    * HS11: USB 2.0 connector USB_E1112 - DISABLED
    * HS12: USB 2.0 connector USB_E1112 - ENABLED (Used for Broadcom bluetooth PCI adapter)
    * HS13: USB 2.0 Reard  - ENABLED
    * HS14: USB 2.0 Reard  - ENABLED
    * SS01: ENABLED
    * SS02: ENABLED
    * SS03: ENABLED
    * SS04: ENABLED
    * SS05: DISABLED
    * SS06: DISABLED
    * SS07: ENABLED
    * SS08: ENABLED
    * SS09: DISABLED
    * SS10: DISABLED
    * Other Super Speed (SS) USB ports are DISABLED 
* Compile as `SSDT-UIAC.aml` file to `EFI/CLOVER/ACPI/patched/`
* Disable USB port limit patch in Clover

```
[File Example](./SSDT/SSDT-UIAC.dsl)
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