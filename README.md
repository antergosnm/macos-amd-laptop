# macos-amd-laptop
Trying to install macOS on my AMD Laptop

## Laptop Spec
Not all AMD laptops will work!!
- AMD Ryzen 7 3700U
- AMD RX Vega 10
- 8GB RAM DDR4 (Dual Channel)
- SATA M.2 512GB WD

## Why Big Sur and not newer?
A developer is trying to create a .kext that allows AMD iGPU to get Graphic Acceleration and for now will only work on Big Sur.

## What bootloader are you using?
OpenCore. I recommend to follow step by step the Dortania's OpenCore guide.

## Progress
- OpenCore boot!
- Installer has appeared!

## Issues
- SATA M.2 drive is not being recognized. For an unknown reason, Apple dropped support for a lot of SATA drivers on Big Sur, and guess what, SATA-Unsupported does not fix it. I tried CtlnaAHCIPort but it does not work (idk why xd).
I'm currently looking for a solution.
- HID Trackpad not working xd.

## Thanks to
- [amd-laptop-hackintosh](https://github.com/iamthaoly/amd-laptop-hackintosh) by iamthaoly
- [Dortania's OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/)
