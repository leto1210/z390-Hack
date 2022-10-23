
## ACPI

SSDT needed:

* ***SSDT-AWAC.aml*** This is the 300 series RTC patch
* ***SSDT-EC-USBX.aml*** Hides the Embedded controller and creates a fake one for macOS, needed for all Catalina users and recommended for other versions of macOS. Also has a second function, USBX. This is used for forcing USB power properties
* ***SSDT-PLUG.aml*** [Allows for native CPU power management](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug-methods/prebuilt.html)
* ***SSDT-PMC.aml*** To enable nvram Z390 support. True 300 series motherboards(non-Z370) don't declare the FW chip as MMIO in ACPI and so XNU ignores the MMIO region declared by the UEFI memory map
* ***SSDT-DMAR.aml*** Fix memory reservation for Wihi and Ethernet workin when Intel VT-d is enabled and system memory is higher > 16G (The network card must be on the second physical PCI slot: PCIEX16_2)
* ***~~SSDT-ASUS-AQUANTIA.aml~~*** ~~Mapping third network card whit Aquantia with the correct PCI Id (The network card must be on the second physical PCI slot: PCIEX16_2)~~


---
#### Patches :

No patches

---
#### Delete :

Drop OEM DMAR Table (working with SSDT-DMAR.aml) - Mandatory for Sonnet Solo10G SFP+ support
