# BIOS settings for installation and boot (eGPU)

***Bios version 0905 (2019/04/11)***

````
Always do a "Load Optimized Defaults" after Bios Update or before applying this parameters
````

## Ai Tweaker

* Ai Overclock Tuner: XMP 1

## Advanced

### Platform Misc Configuration

* PCI Express Native Power Management: Enabled
* NATIVE ASPM: Enabled

### CPU Configguration

* Intel (VMX) Virtualization Technology: Disabled
* CPU Powermanagement Control
	* CFG Lock: Disabled

### Sytem Agent (SA) Configuration

* VT-d: Enabled
* Above 4G Decoding: Enabled
* Memory Configiration
	* Primary Display: PCIE
	* iGPU Monitor: Enabled
	* DVMT Pre-Allocated: 96M
	* RC6 (Render Standby): Disabled

### PCH-FW Configuration

* TPM Device Selection: Discrete TPM

### Onboard Devices Configuration

* HD Audio: Enabled
* Intel Lan Controller: Enabled
	* Intel PXE Option ROM: Disabled
* Serial Port Configuration
	* Serial Port: Off

### Subsystem Settings

* SR-IOV Support: Disabled

### USB Configuration

* Legacy USB Support: Disabled
* XHCI Hand-off: Enabled

### Network Stack Configuration

* Network Stack: Enabled

## Boot

### CSM (Compatibility Support Module)

* Launch CSM: Disabled

### Secure Boot

* OS Type: Other OS
