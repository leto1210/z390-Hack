
## DEVICES


```markup
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
```

---
#### Audio:

Here we set our audio to inject _Layout 7_ - this may or may not be compatible with your codec, but you can check on [_AppleALC's Supported Codec Page_](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs).

We also enabled _ResetHDA_ which puts the codec back in a neutral state between OS reboots. This prevents some issues with no audio after booting to another OS and then back.

