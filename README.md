# HP-EliteDesk-800-G2-DM-Hackintosh
This repository contains the OpenCore EFI to install macOS Monterey on the [HP EliteDesk 800 G2 Desktop Mini PC (35W)](https://support.hp.com/us-en/product/hp-elitedesk-800-35w-g2-desktop-mini-pc/7633266/product-info).
Based on [randyzhong](https://github.com/randyzhong/HP-EliteDesk-800-G2-DM-Hackintosh) version.

[![HP EliteDesk 800 G2 Desktop Mini Business PC](https://ssl-product-images.www8-hp.com/digmedialib/prodimg/lowres/c04876268.png)](https://support.hp.com/us-en/product/hp-elitedesk-800-35w-g2-desktop-mini-pc/7633266/product-info)

## Hardware Specs
### Basic info
Here is my EliteDesk 800 G2 DM 35W specs:
- Product Number: CZC6099PCM
- Product Name: HP EliteDesk 800 G2 DM 35W
- BIOS: 02.53 Rev.A (31 May 2021)

### Specs:
- CPU: Intel® Core i5-6500T @ 2.50 GHz processor
- GPU: Integrated Intel® HD Graphics 530 (2 DisplayPorts + 1 VGA Port)
- Memory: 1 x 8GB DDR4 2133MHz
- Storage: KINGSTON SA2000M8500G
- LAN: Intel® I219-LM GbE
- WLAN: Intel® 8260 802.11ac wireless M.2 with Bluetooth
- Audio: Realtec ALC221 Audio Codec (all ports are stereo, 1 internal speaker, 1 front headphone, 1 front CITA port)

## Configure BIOS Settings
To start, set BIOS to defaults.
Then insure:
- Advanced -> Boot Options
  - Disable **Fast Boot**
  - Disable **CD-ROM Boot**
  - Enable **USB Storage Boot**
  - Disable **Network (PXE) Boot**
  
- Advanced -> Secure Boot Configuration
  - Select **Legacy Support Enable and Secure Boot Disable**, press **F10** to save changes, system will reboot and lead you to Secure Boot and ask you to input a 4 digits security code for authorization, type in the code shows on the screen and enter to reboot and then press **F10** again to enter BIOS configuration

- Advanced -> System Options
  - Disable **Virtualization Technology (VTx)**
  - Disable **Virtualization Technology for Directed I/O (VTd)**
  - Enable **M.2 SSD** if you're using a NVME SSD
  - Check **M.2 WLAN/BT**
  - Check **Allow PCIe/PCI SERR# Interrupt** (Uncheck it if have interruption issues)

#### Advanced -> Built-in Device Options
- Disable **Wake on LAN**
- Set Video memory size to **64MB** or larger
- Disable **LAN/WLAN Auto Switching**
- Disable **Wake on WLAN**

#### Advanced -> Port Options
- Enable **all** if no specific reasons.

#### Advanced -> Power Management Options
- Disable **Extended Idle Power States**

#### Advanced > Option ROM Launch Policy (Dual displays support)
- Configure Option ROM Launch Policy to **All UEI**


Press **F10** to save changes.

### Tested OS
- macOS Monterey 12.1

### Bootloader
- OpenCore 0.7.7

### Kexts
- AirportItlwm (2.0.0)
- AppleALC (1.7.0)
- BluetoothFixup.kext (2.6.1)
- CPUFriend.kext (1.2.4)
- IntelBluetoothFirmware (2.0.1)
- IntelMausi.kext (1.0.7)
- Lilu.kext (1.6.0)
- NVMEFix (1.0.9)
- RTCMemoryFixup.kext (1.0.7)
- SMCSuperIO.kext (1.247)
- SMCProcessor.kext (1.2.7)
- USBPorts.kext (1.0)
- VirtualSMC.kext (1.2.9)
- WhateverGreen.kext (1.5.8)

### USB 3.0 Ports
**USB 2.0 Device**
- HS01: Back left up USB2
- HS02: Back left down USB2
- HS03: Front Left USB2
- HS04: Back right down USB2
- HS05: Back right up USB2
- HS13: Front right USB2

**USB 3.0 Device**
- SS01: Back left up USB3
- SS02: Back left down USB3
- SS03: Front left USB3
- SS04: Back right down USB3
- SS05: Back right up USB3
- SS08: Front right USB3

**Type-C**
- HS09: Front Type-C

**Bluetooth**
- HS07: Internal Intel Bluetooth

## Known Issues:
- VGA port is not supported
- Front Headphone/Mic combo jack is not working
- Sleep is not working (black screen when trying to wake it)
- Upgrades face one time **Real-Time Clock (RTC) Power loss (005)** error, safely ignore it. When upgrade is finished, no RTC erros on normal reboot
- Bluetooth breaks if you turn it off and on and sometimes goes mad, in those cases reboot to make it work again

## Credits:
Thanks to [randyzhong](https://github.com/randyzhong/HP-EliteDesk-800-G2-DM-Hackintosh) and his setup.
