
## ACPI

SSDT needed:
* ***SSDT-AWAC.aml*** This is the 300 series RTC patch
* ***SSDT-EC-USBX.aml*** Hides the Embedded controller and creates a fake one for macOS, needed for all Catalina users and recommended for other versions of macOS. Also has a second function, USBX. This is used for forcing USB power properties
* ***SSDT-PLUG.aml*** Allows for native CPU power management
* ***SSDT-PM.aml*** To enable nvram Z390 support. True 300 series motherboards(non-Z370) don't declare the FW chip as MMIO in ACPI and so XNU ignores the MMIO region declared by the UEFI memory map
* ***SSDT-UIAC.aml*** To restrict USB ports

---
#### Patches :
* ***change EC0 to EC*** To enable USB power management
* ***RTC fix***
* ***change PEPG to GFX0***
* ***change GFX0 to IGPU***
* ***change XHCI to XHC*** Helps avoid a conflict with built-in USB injectors
* ***change SAT0 to SATA*** Need for correct mapping of my SATA drive
* ***change HDAS to HDEF***
