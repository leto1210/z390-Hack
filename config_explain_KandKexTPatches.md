
## Kernel And Kext Patches


```markup
<key>KernelAndKextPatches</key>
	<dict>
		<key>AppleIntelCPUPM</key>
		<true/>
		<key>AppleRTC</key>
		<true/>
	</dict>
```

---
#### Checkboxes:

* _Apple RTC_ - this ensures that we don't have a BIOS reset on reboot.
* _KernelPM_ - this setting prevents writing to MSR 0xe2 which can prevent a kernel panic at boot.
