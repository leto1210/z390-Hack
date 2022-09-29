# z390-Hackintosh based on ***Core i9-9900k | Z390 | RX6600***



Inspiration by [Hackintosh / Vanilla](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/) & [OpenCore Vanilla Guide](https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/) & [CMER Hackintosh based on Gigabyte Z390 Aorus Master](https://github.com/cmer/gigabyte-z390-aorus-master-hackintosh) & [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/) & [Dortania Guide](https://dortania.github.io/OpenCore-Install-Guide/)

Sections:
 * Jump to [Hardware](./Hardware.md)
 	* Jump to [Explain BIOS](./config_explain_BIOS.md)
 * Jump to [Software](./Software.md)
 	* Jump to [Explain ACPI](./config_explain_ACPI.md)
 	* Jump to [Explain BOOT](./config_explain_BOOT.md)
 	* Jump to [Explain DEVICES](./config_explain_DEVICES.md)
 	* Jump to [Explain SSDT USB](./config_ssdt_usb.md)
 * Jump to [Benchmark](./benchmark.md)


![About Mac](./Images/About_10.png)
![About RX6600](./Images/VideoProc_Result_3.png)



## Parts List

[PC PartPicker Part List](https://pcpartpicker.com/list/7hDRr6)

Type|Item
:----|:----
**~~CPU~~** | [~~Intel - Core i7-8700 3.2 GHz 6-Core Processor~~](https://pcpartpicker.com/product/C9hj4D/intel-core-i7-8700-32ghz-6-core-processor-bx80684i78700)
**CPU** | Intel - Core i9-9900k 3.6 GHz 8-Core Processor
**CPU Cooler** | [be quiet! - Dark Rock 4 CPU Cooler](https://pcpartpicker.com/product/FRYLrH/be-quiet-dark-rock-4-cpu-cooler-bk021)
**Motherboard** | [Asus - ROG STRIX Z390-F GAMING ATX LGA1151 Motherboard](https://pcpartpicker.com/product/CM7v6h/asus-rog-strix-z390-f-gaming-atx-lga1151-motherboard-rog-strix-z390-f-gaming)
**Memory** | [Corsair - Vengeance LPX 16 GB (2 x 8 GB) DDR4-3200 Memory](https://pcpartpicker.com/product/DK66Mp/corsair-vengeance-lpx-16-gb-2-x-8-gb-ddr4-3200-memory-cmk16gx4m2d3200c16)
**Memory** | [Corsair - Vengeance LPX 16 GB (2 x 8 GB) DDR4-3200 Memory](https://pcpartpicker.com/product/DK66Mp/corsair-vengeance-lpx-16-gb-2-x-8-gb-ddr4-3200-memory-cmk16gx4m2d3200c16)
**Storage MVNE (for MacOS)** | [Western Digital - SN750 500 GB M.2-2280 Solid State Drive](https://pcpartpicker.com/product/KTQG3C/western-digital-sn750-500-gb-m2-2280-solid-state-drive-wds500g3x0c)
**Storage MVNE (for Win10)** | [Western Digital - Blue SN500 500 GB M.2-2280 Solid State Drive](https://pcpartpicker.com/product/2cJtt6/western-digital-blue-sn500-500-gb-m2-2280-solid-state-drive-wds500g1b0c)
**Storage SATA** | [Seagate FireCuda 1 TB 2.5" 5400RPM Hybrid Internal Hard Drive](https://fr.pcpartpicker.com/product/w6x9TW/seagate-firecuda-1tb-25-5400rpm-hybrid-internal-hard-drive-st1000lx015)
**~~Video Card~~** | ~~[Sapphire - Radeon RX VEGA 56 8 GB PULSE Video Card](https://pcpartpicker.com/product/cKhKHx/sapphire-radeon-rx-vega-56-2gb-pulse-video-card-11276-02-40g)~~
**Video Card** | Sapphire - Radeon RX 6600 Gaming 8 GB PULSE Video Card
**Case** | [NZXT - H500 ATX Mid Tower Case](https://pcpartpicker.com/product/dy66Mp/nzxt-ca-h500b-ow-atx-mid-tower-case-ca-h500b-ow)
**Power Supply** | [SeaSonic - PRIME Ultra Titanium 650 W 80+ Titanium Certified Fully Modular ATX Power Supply](https://pcpartpicker.com/product/fnjJ7P/seasonic-prime-ultra-titanium-650w-80-titanium-certified-fully-modular-atx-power-supply-ssr-650tr)
**Custom** | [ROG Addressable LED Strip (30 cm, Aura Sync RGB, magnetisch Casemod)](https://pcpartpicker.com/product/ytBTwP/rog-addressable-led-strip-30-cm-aura-sync-rgb-magnetisch-casemod)
**Custom** | ~~Airport Bcm94360Cs2 from Macbook Air A1465 on a WiFi Bluetooth 4.0 Wireless Card to PCI-E Adapter with External Antenna~~
**Custom** | Airport Bcm943602CDP from iMac A1418 & A1419 on a WiFi Bluetooth 4.2 Wireless Card to PCI-E Adapter with External Antenna
**Custom** | Sonnet Solo10G SFP+ card


### Working
---
* Monterey install boots successfully
* APFS - NVME - WD Black
* Sata - WD Green
* Sapphire Pulse RX6600 HDMI and Display Port
* Headless iGPU UHD 630
* Wired Ethernet - Intel I219-V PCI Express Gigabit Ethernet
* Wireless Ethernet / Wifi - Airport A1418 (Bcm943602CDP)
* Bluetooth - Airport A1418 (Bcm943602CDP)
* Apple Bluetooth WakeUp
* Audio - Select internal speakers
* Rear and Front audio jacks
* USB 2.0
* Apple Superdrive USB 2.0
* USB 3.1 and USB C
* Sleep/Wake
* Quicklook
* Youtube video
* Netflix with Chrome and Safari
* H.264 videos via VLC (.mkv, .m4a, .m4p)
* HWMonitor
* AirPlay
* Handoff & Continuity
* Facetime
* Itunes
* Apple Store
* Nightshift
* Apple Watch unlock
* Sidecar

### Not Working
---

* NA


### Tools
* [OCAuxiliaryTools - OCAT](https://github.com/ic005k/OCAuxiliaryTools)
* [Hackintoosh](http://headsoft.com.au/download/mac/Hackintool.zip)
* [Kext Updater](https://www.kextupdater.de/)
* [Intel Power Gadget](https://software.intel.com/en-us/articles/intel-power-gadget)
* [LG 4K Dolby Trailer](https://drive.google.com/uc?export=download&id=1Fr_pI7uadSs9K99WFrJx2-1m8GwcC1R9)
* [MacIASL](http://sourceforge.net/projects/maciasl)
* [VideoProc](https://www.videoproc.com/) - Chech UHD Hardware Acceleration
