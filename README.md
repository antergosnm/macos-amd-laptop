![Findericon](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Finder_Icon_macOS_Big_Sur.png/800px-Finder_Icon_macOS_Big_Sur.png)

## Contents
- [Laptop Spec](#laptop-spec)
- [The reason for Big Sur](#the-reason-for-big-sur)
- [Bootloader](#bootloader)
- [Progress](#progress)
- [Issues](#issues)
- [A quick note about a few things](#a-quick-note-about-a-few-things)
- [My USB got corrupted](#my-usb-got-corrupted)
- [Release scheme](#release-scheme)
- [Thanks to](#thanks-to)

## Laptop Spec
Not all AMD laptops will work!!

| Component | Name |
| --- | --- |
| CPU | AMD Ryzen 7 3700U |
| GPU | AMD Radeon RX Vega 10 (Raven) |
| RAM | 8GB DDR4 Dual Channel |
| SSD | 512GB SATA M.2 SSD |
| Screen | 1920x1080p Display |
| TrackPad | HID TrackPad |
| Keyboard | PS2 Keyboard |

## The reason for Big Sur
A developer is trying to create a .kext that allows AMD iGPU to get Graphic Acceleration and for now will only work on Big Sur.

## Bootloader
OpenCore. I recommend to follow step by step the Dortania's OpenCore guide.

## Progress
- [x] OpenCore boot!
- [x] Installer has appeared!
- [x] Install successful
- [x] Booted the installation
- [x] Using it as normal (no GPU Acceleration)
- [x] Testing GPU Acceleration kext

## Issues
- ~~SATA M.2 drive is not being recognized. For an unknown reason, Apple dropped support for a lot of SATA drivers on Big Sur, and guess what, SATA-Unsupported does not fix it. I tried CtlnaAHCIPort but it does not work (idk why xd).
I'm currently looking for a solution.~~
- ~~HID Trackpad not working xd.~~

## A quick note about a few things
When I release a EFI folder, if try to boot without touching anything it will result on an error saying that macOS can't be installed on that product, that's because I delete the product info on the config.plist (EFI/OC/config.plist). Solving this is pretty easy:
- You'll need **GenSMBIOS** to generate a new SMBIOS (python has to be installed).
- When GenSMBIOS opens, choose option 1 and press enter, after that, choose option 3.
- You will generate this model: `iMacPro1,1`
- This table shows where to put each value of the GenSMBIOS generated:

| Value | Place |
| --- | --- |
| `Type` | ProductInfo > Generic > SystemProductName |
| `Serial` | ProductInfo > Generic > SystemSerialNumber |
| `Board Serial` | ProductInfo > Generic > MLB |
| `SmUUID` | ProductInfo > Generic > SystemUUID |
| `Apple ROM` | ProductInfo > Generic > ROM |

That should do the job.

## My USB got Corrupted
This can happen because OpenCore didn't boot as intended, it can corrupt your USB stick, you will notice this because you can't delete or add files in certain directories inside the EFI folder.

At this point you should remake your USB and find out if your BIOS is set up correctly, or if some .kext has ocassionated the issue.

## Thanks to
- [amd-laptop-hackintosh](https://github.com/iamthaoly/amd-laptop-hackintosh) by [iamthaoly](https://github.com/iamthaoly)
- [Dortania's OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/)
