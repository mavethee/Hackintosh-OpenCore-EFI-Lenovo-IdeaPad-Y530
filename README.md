<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

## Hackintosh-OpenCore-Lenovo-IdeaPad-Y530
EFI premade of OpenCore bootloader for Lenovo IdeaPad Y530 is here!

## Current version - OpenCore 0.8.9 DEBUG
Repository contains full ,,Plug-and-Play" EFI of OpenCore bootloader and
all needed files to install and run macOS on Lenovo IdeaPad Y530!

https://github.com/acidanthera/OpenCorePkg/releases/tag/0.8.9

And friendly advice! Upgrade CPU to something like T9800, add as much RAM as possible and use SATA SSD to not suffer! :D

<img src="https://preview.redd.it/wp2b2vzb1ve81.png?width=1280&format=png&auto=webp&s=73d326b69f5c674904c37b29f209e364bb431996">
<img src="https://preview.redd.it/8y88s387qlj81.png?width=1280&format=png&auto=webp&s=7d40c3a5b686a2173fd3e9843798aef74f4cac38">

### General note:

1. IMPORTANT THIS IS LEGACY SYSTEM! YOU NEED TO CREATE YOUR OWN boot file (for both USB and EFI inside HDD/SSD later on):

* Using Windows:

    https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html#diskpart-method

2. Using macOS:

    https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#legacy-setup


3. I've used Nvidia GeForce 9600M GS in IdeaPad Y530 with Core2 Duo T6500 CPU, so it might not really work for you, if it isn't, just follow this (!DO IT BEFORE INSTALLING MACOS!):

    - Legacy Nvidia Patching Guide:
        
        https://dortania.github.io/OpenCore-Post-Install/gpu-patching/nvidia-patching/

    - 9600M GS ROM (use latest Lenovo one):

        https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=9600M+GS&interface=&memType=&memSize=&since=

### SMBIOS:
Present in repo SMBIOS is not purchased Apple's device but for own sake, I don't advice you to use it.
...for own sake ;)

To generate SMBIOS you can use:

* GenSMBIOS:

    https://github.com/corpnewt/GenSMBIOS

Tool doesn't matter really, you just need not valid or unused SMBIOS to copy-paste needed info.
...if you wish to use iServices of course :)

### High Sierra note: 
* To make my Intel WiFi card working I've used j137 for SecureBootModel, if you have issues like throwing back to boot picker, please follow this troubleshooting in Recovery:
    
    https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#special-notes-with-securebootmodel

### Monterey note:

See current issues and workarounds: https://github.com/dortania/OpenCore-Legacy-Patcher/issues/108#issuecomment-810634088

!To resolve most Tesla issues in latest macOS related to lack of acceleration and Metal, after patching you also make sure to:

1. Disable Apple Secure Boot, which requires:
- Allow loading unsigned DMGs (`Misc -> Security -> DmgLoading -> Any`)
- Disable Apple Secure Boot (`Misc -> Security -> SecureBootModel -> Disabled`)

2. Set custom SIP to 0x802 (`NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> csr-active-config` set to `02080000`)

3. Disable AMFI: 
    - Fully disable AMFI (`NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args -> amfi=0x80`)
    - For macOS 12.3+, Apple broke something when AMFI is disabled and SIP is off or custom, just add this `ipc_control_port_options=0` to boot-args after AMFI boot-arg.

4. For macOS 12.4+, you also need a NoAVXFSCompressionTypeZlib kext to downgraade APFS compression Type Zlib to not require AVX1.0 just as it was in 12.3.1!

5. From macOS recovery after macOS is installed, make sure to navigate to Utilities -> Terminal and run "csrutil disable --no-internal" and "csrutil authenticated-root disable"

6. Run OpenCore Legacy Patcher 0.5.2 (If for some reason, you wanna run older versions, 0.4.5+ is reccomended minimum due to kext for checking for OCLP updates applied and recent Non-Metal fixes, see #108)

### Ventura note:
As of OpenCore Legacy Patcher 0.6.0+, non-Metal is here again on Ventura! :D

https://github.com/dortania/OpenCore-Legacy-Patcher/releases/

!CLEAN INSTALL IS HIGHLY RECCOMENDED!

1. Change SMBIOS to Ventura supported one (See SMBIOS section, I reccommend `MacBookPro14,3`)

2. Disable Apple Secure Boot, which requires:
- Allow loading unsigned DMGs (`Misc -> Security -> DmgLoading -> Any`)
- Disable Apple Secure Boot (`Misc -> Security -> SecureBootModel -> Disabled`)

3. Set custom SIP to 0x803 (`NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> csr-active-config` set to `03080000`)

4. Disable AMFI: 
    - Fully disable AMFI (`NVRAM -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args -> amfi=0x80`)
    - For macOS 12.3+, Apple broke something when AMFI is disabled and SIP is off or custom, just add this `ipc_control_port_options=0` to boot-args after AMFI boot-arg.

5. For 12.4+ Zlib compression fix, we need to add to the combo `NoAVXFSCompressionTypeZlib-AVXpel` kext, to resolve Zlib-based instability in Ventura on pre-Sandy Bridge.

    https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Misc/NoAVXFSCompressionTypeZlib-AVXpel-v12.6.zip

6. Since 13.0, Apple requires AVX2 to even be able to boot, we need to use `CryptexFixup` kext to use Rosetta 2 dyids which lacks of AVX2 as well.

    https://github.com/acidanthera/CryptexFixup/

7. Replace Intel WiFi kext to 2.2.0 which is in ALPHA still but reuired for Ventura!

    https://github.com/OpenIntelWireless/itlwm/releases/tag/v2.2.0-alpha


8. From macOS recovery after macOS is installed, make sure to navigate to Utilities -> Terminal and run "csrutil disable --no-internal" and "csrutil authenticated-root disable"

You are on your own with this one!


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
- NVRAM, will take a look at it finally but it will eventually take time.

## Credits:
### Airportitlwm:
https://github.com/OpenIntelWireless/itlwm
### AutoPkgInstaller:
https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AutoPkgInstaller-v1.0.1-DEBUG.zip
### AppleALC:
https://github.com/acidanthera/AppleALC
### BCM5722D:
https://github.com/chris1111/BCM5722D/releases
### Lilu:
https://github.com/acidanthera/Lilu/
### NoAVXFSCompressionTypeZlib (for 12.4+):
https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Misc/NoAVXFSCompressionTypeZlib-v12.3.1.zip
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
