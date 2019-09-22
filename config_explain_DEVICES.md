
## DEVICES


```markup
<key>Devices</key>
	<dict>
		<key>Properties</key>
		<dict>
			<key>PciRoot(0x0)/Pci(0x1f,0x3)</key>
			<dict>
				<key>AAPL,slot-name</key>
				<string>Internal</string>
				<key>device-id</key>
				<data>
				cKEAAA==
				</data>
				<key>device_type</key>
				<string>Audio device</string>
				<key>hda-gfx</key>
				<string>onboard-1</string>
				<key>layout-id</key>
				<data>
				AQAAAA==
				</data>
				<key>model</key>
				<string>Cannon Lake PCH cAVS</string>
			</dict>
		</dict>

```

---
#### Audio:

Here we set our audio to inject _Layout 1_ - this may or may not be compatible with your codec, but you can check on [_AppleALC's Supported Codec Page_](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs).

Asus ROG SupremeFX S1220A is base on Realteck ALC1220.
Acording to Info.plist on AppleALC Github for ALC1220 layout 1 is for "Toleda - Realtek ALC1220, 5/6 audio ports, native: 2 inputs, 3/4 outputs+front panel+SPDIF/Optical"


#### Graphics:

No special setup