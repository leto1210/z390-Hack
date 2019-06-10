
## BOOT


```markup
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
```

---
#### Arguments (by [Hackintosh / Vanilla](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/)):

We have a few boot args set here:

* `-v` - this enables verbose mode, which shows all the _behind-the-scenes_ text that scrolls by as you're booting instead of the Apple logo and progress bar.  It's invaluable to any Hackintosher, as it gives you an inside look at the boot process, and can help you identify issues, problem kexts, etc.
* `dart=0` - this is just an extra layer of protection against Vt-d issues.
* `debug=0x100` - this prevents a reboot on a kernel panic.  That way you can \(hopefully\) glean some useful info and follow the breadcrumbs to get past the issues.
* `keepsyms=1` - this is a companion setting to `debug=0x100` that tells the OS to also print the symbols on a kernel panic.   That can give some more helpful insight as to what's causing the panic itself.
* `shikigva=40` - this flag is specific to the iGPU.  It enables a few _Shiki_ settings that do the following \(found [_here_](https://github.com/acidanthera/WhateverGreen/blob/master/WhateverGreen/kern_shiki.hpp#L35-L74)\):
  * `8 - AddExecutableWhitelist` - ensures that processes in the whitelist are patched.
  * `32 - ReplaceBoardID` - replaces board-id used by AppleGVA by a different board-id.

