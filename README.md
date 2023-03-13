![Findericon](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Finder_Icon_macOS_Big_Sur.png/800px-Finder_Icon_macOS_Big_Sur.png)

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
- [x] OpenCore boot!
- [x] Installer has appeared!
- [ ] Install successful
- [ ] Booted the installation
- [ ] Using it as normal (no GPU Acceleration)
- [ ] Testing GPU Acceleration kext

## Issues
- SATA M.2 drive is not being recognized. For an unknown reason, Apple dropped support for a lot of SATA drivers on Big Sur, and guess what, SATA-Unsupported does not fix it. I tried CtlnaAHCIPort but it does not work (idk why xd).
I'm currently looking for a solution.
- HID Trackpad not working xd.

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

## Release scheme
Every time I make a change which result successful I'll release my EFI folder without the Product info on the config.plist.
Releases can have this tags: 
- **TestVer**: Used for releases with changes that are under testing and may be unstable or have issues not discovered.
- **RfR**: Ready for Release will have the most stable changes to the files.
- **HotFix**: This means I made a mistake and I quickly fixed it.

## Thanks to
- [amd-laptop-hackintosh](https://github.com/iamthaoly/amd-laptop-hackintosh) by [iamthaoly](https://github.com/iamthaoly)
- [Dortania's OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/)
