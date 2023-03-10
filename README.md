# ASUS A556U (X556UQ) - Hackintosh Catalina 10.15.5 - Big Sur 11.5.1 (OpenCore)

---

### Screenshot

---

- Big Sur 11.5.1 (Update)

![](Screenshot/Screen%20Shot%202021-08-03%20at%2012.11.47.png)

- Big Sur 11.2.3 (Update)

![](Screenshot/Screen%20Shot%202021-03-13%20at%2003.58.45.png)

- Big Sur 11.0.1 (Update)

![](Screenshot/Screen%20Shot%202021-03-13%20at%2003.58.45.png)

- Catalina 10.15.6 (Update)

![](Screenshot/Screen%20Shot%202020-08-01%20at%2012.42.25.png)

- Catalina 10.15.5

![](Screenshot/Screen%20Shot%202020-07-31%20at%2022.21.11.png)

![](Screenshot/Screen%20Shot%202020-07-31%20at%2022.25.22.png)

![](Screenshot/Screen%20Shot%202020-07-31%20at%2022.27.29.png)

![](Screenshot/Screen%20Shot%202020-07-31%20at%2022.28.18.png)

### Technical Specifications

---

| Name              | Specifications                                                                                                                           |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Processor         | Intel Core i5 - 6200U                                                                                                                    |
| Memory            | 1x 4 GB DDR4 2133 Mhz + 1x 8 GB DDR4 2133 Mhz                                                                                            |
| Storage           | SSD M.2 SATA Silicon Power 240 GB                                                                                                        |
| Video             | Integrated Intel HD 520 + NVIDIA 940MX                                                                                                   |
| Wi-Fi + Bluetooth | ~~Qualcomm Atheros 9565~~┬áReplaced by BCM94360NG                                                                                         |
| Ethernet          | Realtek RTL8111                                                                                                                          |
| Audio             | Realtek ALC255                                                                                                                           |
| Touchpad          | ELAN 1000 I2C Interface                                                                                                                  |
| Screen Size       | 15,6 Inch                                                                                                                                |
| Screen Resolution | 1920 x 1080                                                                                                                              |
| Others            | 1x Card Reader, 1x WebCam, 1x VGA Port, 1x HDMI, 1x Combo Audio Jack, 1x USB 2.0, 1x USB 3.0 Type A, 1x USB 3.0 Type C,┬á1x Optical Drive |

### What Works Well

---

Ôťů Intel HD 520 (With QE/CI)

Ôťů All USB Port

Ôťů VGA Port

Ôťů Keyboard

Ôťů Touchpad

Ôťů Onboard Ethernet

Ôťů Webcam

Ôťů Battery Status

Ôťů FN Keys (Almost all key working)

Ôťů Native Power Management

Ôťů Optical Drive

Ôťů Restart, Sleep, Shutdown

Ôťů Wifi and Bluetooth

### What Works (with Notes)

---

ÔÜá´ŞĆ Audio (Internal mic work but not auto switchable)

~~ÔÜá´ŞĆ Bluetooth (Boot to Windows/Linux/VM to load firmware) [AR9565]~~

ÔÜá´ŞĆ ~~Wi-Fi (Cosmetically I notice the WiFi signal tree will randomly drop down to one or no bars and randomly full strength. Allthough this happens I saw no performance drops when this happens.) [AR9565]~~

### Does Not Work

---

ÔŁî NVIDIA 940MX (Optimus - impossible to get working at the moment)

ÔŁî iMessage (TODO fix)

ÔŁî FaceTime (TODO fix)

### Not Tested

---

1. SD Card Reader

2. HDMI

### Kexts List

---

- **OC/Kexts**
  
  [Lilu](https://github.com/acidanthera/Lilu)
  
  [AppleALC](https://github.com/acidanthera/AppleALC)
  
  [AsusSMC (Need Patch DSDT/SSDT)](https://github.com/hieplpvip/AsusSMC)
  
  [CPUFriend](https://github.com/acidanthera/CPUFriend) + [CPUFriendDataProvider](https://www.olarila.com/topic/5693-guide-ssdt-with-pikes-pm-script-and-use-with-cpufriend/)
  
  ~~NoTouchID~~
  
  [RealtekRTL8111](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/)
  
  [VirtualSMC + All Plugins](https://github.com/acidanthera/VirtualSMC)
  
  [VoodooPS2Controller ](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/)
  
  [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
  
  [VoodooI2C + VoodooI2CELAN (Need GPIO Pinning)](https://github.com/alexandred/VoodooI2C)
  
  ~~[HS80211Family.kext + AirPortAtheros40.kext (ATH9565)](https://www.insanelymac.com/forum/files/file/1008-io80211family-modif/)~~
  
  [VerbStub](https://github.com/hackintosh-stuff/ComboJack)
  
  USBMap.kext (Generated by [USBMap](https://github.com/corpnewt/USBMap))

### SSDT Patch

---

- **OC/ACPI**
  
  **SSDT-ATK-BDW** - To remapping Fn Key (AsusSMC only fix Fn volume)
  
  **SSDT-dGPU-Off** - To disable dGPU
  
  **SSDT-EC-USBX** - Fixing Embedded Controller
  
  **SSDT-I2C** - Patch VoodooI2C also GPIO Pinning
  
  **SSDT-I2CBUS** - Potential fix trackpad randomly stopped
  
  **SSDT-PLUG** - Fixing Power Management
  
  **SSDT-PNLF** - Fixing brightness
  
  **SSDT-SBUS-MCHC** - Fixing SMBus support
  
  ~~**SSDT-UIAC** - To remapping USB Port (Generated by [USBMap](https://github.com/corpnewt/USBMap))~~
  
  **SSDT-XOSI** - Change _OSI to XOSI

---

**<mark>Note : </mark>**

- The compiled SSDT patch has not used checking `If (_OSI ("Darwin")) {}`, so it might affect other operating systems when using dual boot / more. (but I only use single boot only)

- Just activate one of the VoodooInput from VoodooI2C or VoodooPS2Controller in config.plist (so that it doesn't conflict)

- In macOS Big Sur. Internal mic works, but mic for combo jack doesn't work (in previous macOS version it works). for workaround you can follow the following tutorial [ComboJack support for ALC256/ALC255](https://github.com/hackintosh-stuff/ComboJack)

- ~~You need to disable ATH9Injector.kext and IO80211Family.kext on config.plist to prevent kernel panic when updating MacOS then enable again after update. [AR9565]~~

- Starting from opencore version `0.7.2` there is additional option to set `minDate` (minimum allowed APFS driver date) and `minVersion` (minimum allowed APFS driver version). By default it will be set to 0 for security purposes. but it should be noted if you use an operating system below the bigsur version and use the default value. you can see it in more detail in the opencore configuration documentation.

---

### Credits

Thanks to everyone who made this possibile: RehabMan, alexandred, black-dragon74, Mieze, acidanthera, every contributor to the repos/guides and the whole Hackintosh community.
