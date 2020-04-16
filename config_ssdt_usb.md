# SSDT (USB)

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
* Compile as `SSDT-UIAC.aml` file to `EFI/ACPI/`
* Disable USB port limit patch in OpenCore

```
[File Example](./SSDT/SSDT-UIAC.dsl)
```


> If you prefer, Hackintool can generate the right files for you ;-)
