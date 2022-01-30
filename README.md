<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

## Hackintosh-OpenCore-Lenovo-IdeaPad-Y530
EFI premade of OpenCore bootloader for Lenovo IdeaPad Y530 is here!

## Current version - OpenCore 0.7.7 (11th January 2022!)
Repository contains full ,,Plug-and-Play" EFI of OpenCore bootloader and
all needed files to install and run macOS on Lenovo IdeaPad Y530!
ONLY TESTED WITH HIGH SIERRA! 10.14+ DOES NOT WORK!

https://github.com/acidanthera/OpenCorePkg/releases/tag/0.7.7

### Please note:
Since OC 0.6.5, I decided to switch to RELEASE version, if you expierience any issues, switch to debug using Dortania's Guide:

https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html

IMPORTANT THIS IS LEGACY SYSTEM! I'VE INCLUDED MY boot FILE BUT YOU MIGHT NEED TO CREATE YOUR OWN (for both USB and EFI inside HDD/SSD later on):
Using Windows: https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html#diskpart-method
Using macOS: https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#legacy-setup


I've used Nvidia GeForce 9600M GS in IdeaPad Y530 with Core2 Duo T6500 CPU, so it might not really work for you, if it isn't, just follow this:
https://dortania.github.io/OpenCore-Post-Install/gpu-patching/nvidia-patching/

9600M GS ROM (use latest Lenovo one):
https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=9600M+GS&interface=&memType=&memSize=&since=

To make my Intel WiFi card working I've used j137 for SecureBootModel, if you have issues like throwing back to boot picker, please follow this troubleshooting in Recovery:
https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#special-notes-with-securebootmodel

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
### OpenCanopy's resources:
https://github.com/acidanthera/OcBinaryData
 
