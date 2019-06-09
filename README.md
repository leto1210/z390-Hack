# z390-Hack based on ***Core i7-8700 | Z390 | VEGA56***

Inspiration by [Hackintosh / Vanilla](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/)

![About](./Images/About.jpg)

# Hardware
## Parts List
[PC PartPicker Part List](https://pcpartpicker.com/list/7hDRr6)

Type|Item
:----|:----
**CPU** | [Intel - Core i7-8700 3.2 GHz 6-Core Processor](https://pcpartpicker.com/product/C9hj4D/intel-core-i7-8700-32ghz-6-core-processor-bx80684i78700)
**CPU Cooler** | [be quiet! - Dark Rock 4 CPU Cooler](https://pcpartpicker.com/product/FRYLrH/be-quiet-dark-rock-4-cpu-cooler-bk021) 
**Motherboard** | [Asus - ROG STRIX Z390-F GAMING ATX LGA1151 Motherboard](https://pcpartpicker.com/product/CM7v6h/asus-rog-strix-z390-f-gaming-atx-lga1151-motherboard-rog-strix-z390-f-gaming)
**Memory** | [Corsair - Vengeance LPX 16 GB (2 x 8 GB) DDR4-3200 Memory](https://pcpartpicker.com/product/DK66Mp/corsair-vengeance-lpx-16-gb-2-x-8-gb-ddr4-3200-memory-cmk16gx4m2d3200c16) 
**Storage MVNE (for MacOS)** | [Western Digital - SN750 500 GB M.2-2280 Solid State Drive](https://pcpartpicker.com/product/KTQG3C/western-digital-sn750-500-gb-m2-2280-solid-state-drive-wds500g3x0c)
**Storage MVNE (for Win10)** | [Western Digital - Blue SN500 500 GB M.2-2280 Solid State Drive](https://pcpartpicker.com/product/2cJtt6/western-digital-blue-sn500-500-gb-m2-2280-solid-state-drive-wds500g1b0c)
**Storage SATA** | [Western Digital - Red 3 TB 3.5" 5400RPM Internal Hard Drive](https://pcpartpicker.com/product/7sTmP6/western-digital-internal-hard-drive-wd30efrx)
**Storage SATA** | [Western Digital - Red 3 TB 3.5" 5400RPM Internal Hard Drive](https://pcpartpicker.com/product/7sTmP6/western-digital-internal-hard-drive-wd30efrx)
**Video Card** | [Sapphire - Radeon RX VEGA 56 8 GB PULSE Video Card](https://pcpartpicker.com/product/cKhKHx/sapphire-radeon-rx-vega-56-2gb-pulse-video-card-11276-02-40g)
**Case** | [NZXT - H500 ATX Mid Tower Case](https://pcpartpicker.com/product/dy66Mp/nzxt-ca-h500b-ow-atx-mid-tower-case-ca-h500b-ow)
**Power Supply** | [SeaSonic - PRIME Ultra Titanium 650 W 80+ Titanium Certified Fully Modular ATX Power Supply](https://pcpartpicker.com/product/fnjJ7P/seasonic-prime-ultra-titanium-650w-80-titanium-certified-fully-modular-atx-power-supply-ssr-650tr)
**Custom** | [Fenvi Desktop Wireless Network M.2(NGFF) Wireless Card to PCI-e 1X Adapter Converter(Not Including Networking card) Compact Intel NGFF M.2 7260 8260 3160 ect Windows 7, 8, 10 Compatible](https://pcpartpicker.com/product/rpgzK8/fenvi-desktop-wireless-network-m2ngff-wireless-card-to-pci-e-1x-adapter-converternot-including-networking-card-compact-intel-ngff-m2-7260-8260-3160-ect-windows-7-8-10-compatible)
**Custom** | [ROG Addressable LED Strip (30 cm, Aura Sync RGB, magnetisch Casemod)](https://pcpartpicker.com/product/ytBTwP/rog-addressable-led-strip-30-cm-aura-sync-rgb-magnetisch-casemod)

## H500 USB
Front panel USB uses 3.0 Gen1 instead of 3.0 Gen2.

## Fan Situation
Location|Fan|Size|RPM|dbA
:----|:----|:----|:----|:----
CPU Cooler (NH-D15) | NF-A15 PWM | 120mm | 300-1400 | 21.4 
Rear (Exhaust) | NZXT Aer F120  PWM | 120mm | 500-1500 | 22 - 31 
Top Rear (Exhaust) | NZXT Aer F120  PWM | 120mm | 500-1500 | 22 - 31

## Asus Z390-F Hardware Info


***Physical View***

![MB Mapping](./Images/MB_InsideView_Annot.jpg) | ![Rear Mapping](./Images/MB_RearView_Annot.jpg)

***USB Mapping*** for each port identified in the bios

Physical Port | Logical Port | Comment
--------------|--------------|--------
G31G2_1       | HS01         | USB 3.1 Gen 2
G31G2_2       | HS02         | USB 3.1 Gen 2
G31G2_3       | HS03         | USB 3.1 Gen 2
G31G2_C4      | HS04         | USB 3.1 Gen 2 Type C + Switch
G31G1_C5      | HS05         | USB 3.1 Gen 2 Type C + Switch
G31G1_7       | HS07         | USB 3.1 Gen 1 Front case
G31G1_8       | HS08         | USB 3.1 Gen 1 Front case
G31G1_9       | HS09         | USB 3.1 Gen 1
USB10         | HS010        | USB 3.1 Gen 1
USB11         | HS011        | USB 2.0
USB12         | HS012        | USB 2.0
USBE12        | HS06         | Internal Aura USB 2.0 Hub
USB13         | HS013        | USB 2.0 Only
USB14         | HS014        | USB 2.0 Only



## BIOS settings for installation and boot (eGPU)


## Create macOS Installation
macOS Mojave version 10.14.5
* Format USB (minimum 8 GB) `diskutil eraseDisk JHFS+ USB /dev/disk#`
> The above command was required for a USB drive which did not have an EFI partition, not created with the GUID partition scheme. The option to create the GUID partition scheme was not in the Mojave Disk Utility GUI.
* Create a macOS USB installer `sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/USB`
* Install Clover to USB installer
* Run Clover Configurator to create/update EFI partition, or copy EFI folder here to the EFI partition


## Config.plist


