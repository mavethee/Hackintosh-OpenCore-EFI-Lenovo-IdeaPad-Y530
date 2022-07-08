<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

## Hackintosh-OpenCore-Lenovo-IdeaPad-Y530
EFI premade of OpenCore bootloader for Lenovo IdeaPad Y530 is here!

## Current version - OpenCore 0.7.8
Repository contains full ,,Plug-and-Play" EFI of OpenCore bootloader and
all needed files to install and run macOS on Lenovo IdeaPad Y530!


And friendly advice! Upgrade CPU to something like T9800, add as much RAM as possible and use SATA SSD to not suffer! :D

<img src="https://preview.redd.it/wp2b2vzb1ve81.png?width=1280&format=png&auto=webp&s=73d326b69f5c674904c37b29f209e364bb431996">
<img src="https://preview.redd.it/8y88s387qlj81.png?width=1280&format=png&auto=webp&s=7d40c3a5b686a2173fd3e9843798aef74f4cac38">

### General note:
Since OC 0.6.5, I decided to switch to RELEASE version, if you expierience any issues, switch to debug using Dortania's Guide or OCAT linked below in SMBIOS section:

https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html

IMPORTANT THIS IS LEGACY SYSTEM! I'VE INCLUDED MY boot FILE BUT YOU MIGHT NEED TO CREATE YOUR OWN (for both USB and EFI inside HDD/SSD later on):

Using Windows: 
https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html#diskpart-method

Using macOS: 
https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#legacy-setup


I've used Nvidia GeForce 9600M GS in IdeaPad Y530 with Core2 Duo T6500 CPU, so it might not really work for you, if it isn't, just follow this (!DO IT BEFORE INSTALLING MACOS!):

https://dortania.github.io/OpenCore-Post-Install/gpu-patching/nvidia-patching/

9600M GS ROM (use latest Lenovo one):

https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=9600M+GS&interface=&memType=&memSize=&since=

HIGH SIERRA NOTE: To make my Intel WiFi card working I've used j137 for SecureBootModel, if you have issues like throwing back to boot picker, please follow this troubleshooting in Recovery:

https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#special-notes-with-securebootmodel

### Monterey note:

!To resolve most Tesla issues in latest macOS related to lack of acceleration and Metal, after patching you also make sure to:

* Set NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> csr-active-config set to "030A0000"

* Disable AMFI (NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args -> Add "amfi_get_out_of_my_way=1")

* From macOS recovery after macOS is installed, make sure to navigate to Utilities -> Terminal and run "csrutil disable --no-internal" and "csrutil authenticated-root disable"

* Run OpenCore Legacy Patcher, GUI prefered if you don't sure what you're doing for baby steps (especially version 0.4.3+ is advised since it fixes a lot of issues with Tesla)

### Whats working?
- Apple Secure Boot (j137) (High Sierra only, in Monterey better to have it disabled because of Non Metal GPU Acceleration patches)
- Intel WiFi card (for High Sierra only with SBM set on j137 and enabled in Kernel -> Force, in Monterey no issues with SBM disabled and enabled in Kernel -> Force)
- Broadcom Ethernet card
- iServices (check SMBIOS tab)
- USB ports
- CD/DVD tray

### Whats not working?
- Audio (tried every ALCID for ALC888, no luck)
- SD Card slots, thats pretty much expected
- Fans monitoring
- Trackpad acts weirdly? I've just used USB mouse :P

### SMBIOS:
Present in repo SMBIOS is not purchased Apple's device but for own sake, I don't advice you to use it.
...for own sake ;)

To generate SMBIOS you can use:
* GenSMBIOS:
https://github.com/corpnewt/GenSMBIOS
* OpenCore Auxiliary Tools:
https://github.com/ic005k/QtOpenCoreConfig

Tool doesn't matter really, you just need not valid or unused SMBIOS to copy-paste needed info.
...if you wish to use iServices of course :)

## Credits:
### Airportitlwm:
https://github.com/OpenIntelWireless/itlwm
### AppleALC:
https://github.com/acidanthera/AppleALC
### BCM5722D:
https://github.com/chris1111/BCM5722D/releases
### HibernationFixup:
https://github.com/acidanthera/HibernationFixup
### IntelBluetoothFirmware:
https://github.com/OpenIntelWireless/IntelBluetoothFirmware
### Lilu:
https://github.com/acidanthera/Lilu/
### OpenCorePkg:
https://github.com/acidanthera/OpenCorePkg/
### OpenCanopy's resources:
https://github.com/acidanthera/OcBinaryData
### OpenCore Legacy Patcher:
https://github.com/dortania/OpenCore-Legacy-Patcher
### Telemetrytrap (for 10.14 and newer):
https://forums.macrumors.com/threads/mp3-1-others-sse-4-2-emulation-to-enable-amd-metal-driver.2206682/post-28447707
### USBInjectAll:
https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads
### VirtualSMC:
https://github.com/acidanthera/VirtualSMC
### VoodooInput:
https://github.com/acidanthera/VoodooInput
### VoodooPS2:
https://github.com/acidanthera/VoodooPS2
### WhateverGreen:
https://github.com/acidanthera/WhateverGreen
