# Acer Aspire VX15 Hackintosh

If you want to use Clover see here:  
https://github.com/dongcodebmt/VX5-591G-Hackintosh

__My Specs__

| Specs | Details |
|------------|-------------------------------|
| Model | Acer Aspire VX15 (VX5-591G) |
| OS | macOS Catalina 10.15.4 |
| CPU | Intel(R) Core(TM) i5 7300HQ |
| RAM | 16 GB DDR4 2400MHz |
| iGPU | Intel HD Graphics 630 |
| dGPU | NVIDIA GeForce GTX 1050M |
| Touchpad | ELAN 0501 |
| Wireless | Intel® Dual Band Wireless-AC 7265 |
| Audio | ALC255 |

![Specs](/image.png)

__Tested and working__

- [x] Intel HD Graphics 630
- [x] USB
- [x] Webcam
- [x] HDMI + HDMI Audio
- [x] LAN
- [x] Screen brightness
- [x] Battery status
- [x] Sleep/Wake
- [x] Audio + Headphone + Internal Mic
- [x] TouchPad with gestures
- [x] Keyboard with backlight (Some function keys not work)
- [x] Bluetooth (Can't off) 

__Not tested__

- [ ] USB C (I don't have a device to test)

__Not working__

- [ ] NVIDIA GeForce GTX 1050M
- [ ] SD Card reader
- [ ] WiFi
- [ ] and a few other minor bugs

For wifi and bluetooth to work you need to replace another wireless card

## Guide

__BIOS Settings (Version 1.08)__

- Set Supervisor Password
- Disable Password on Boot
- Disable Secure Boot
- Set touchpad: Advance

__OpenCore config__

Follow these instructions to configure your OpenCore:  
https://github.com/dortania/vanilla-laptop-guide  
- For touchpad use patch `SSDT-XOSI.aml` and rename XOSI
- I use `alcid=29` it seems fine, however I have not tried it with the headphone jack yet. If that doesn't work, try `alcid=30` 
- For power management, create your own CPUFriend

__Fix brightness key__

Use patch `SSDT-Q11-Q12.aml`  
And at `Root > ACPI > Patch`:  
- XQ11 Rename

|Key|Type|Value|
|---|---|---|
|Comment|String|Change _Q11 to XQ11 (Brightness Down)|
|Count|Number|0|
|Enabled|Boolean|True|
|Find|Data|5F513131|
|Limit|Number|0|
|Replace|Data|58513131|

- XQ12 Rename

|Key|Type|Value|
|---|---|---|
|Comment|String|Change _Q12 to XQ12 (Brightness Up)|
|Count|Number|0|
|Enabled|Boolean|True|
|Find|Data|5F513132|
|Limit|Number|0|
|Replace|Data|58513132|

__Fix Timezone (Dual Boot)__

See: https://www.tonymacx86.com/threads/fix-incorrect-time-in-windows-osx-dual-boot.133719/
## Credits

Thanks to Acidanthera, dortania, alexandred

*__Enjoy__*
