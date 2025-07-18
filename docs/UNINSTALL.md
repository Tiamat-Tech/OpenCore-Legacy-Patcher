# Uninstall

This guide tells you different ways to uninstall OCLP and/or patches.

## Delete everything and revert back to native macOS

1. Create a USB drive with the latest officially supported macOS installer.
2. Restart the computer and [Reset NVRAM.](https://support.apple.com/HT204063)
3. Boot the computer using the installer USB drive.
4. Go to Disk Utility and choose View -> Show All Devices.
5. Wipe the full disk by choosing the top disk option on the left sidebar and selecting "Erase".
6. Start macOS installation.

## Manual methods

Uninstalling OCLP manually is a three part process which includes the application, OpenCore and the root patches. If you want to remove OCLP and patches entirely, go through all three in succession. Otherwise do the part(s) you need.

### Reverting root patches

Open the OCLP application and go into the Post Install Root Patch menu, choose Revert Root Patches. 

*  **Supported on Monterey and later. Big Sur does not support snapshot reversion and requires a reinstall. Reinstall can be done without a wipe if the macOS installer version used is the same or newer.**

### Uninstalling the application

To uninstall the OCLP application including LaunchAgent and PrivilegedHelperTool, download the uninstaller package from [the releases page.](https://github.com/dortania/OpenCore-Legacy-Patcher/releases)

### Uninstalling the bootloader

1. Remove OpenCore either from the USB or internal drive

  * Mount the drive's EFI partition, and delete the `EFI/OC` and `System` folders
    * Note: **Do not** delete the entire EFI folder, this will likely break any existing Windows and Linux installations.
    * [See here for an example on how to mount](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html)
    * 5K iMac users, also delete `boot.efi` on the root of the EFI partition.

2. [Reset NVRAM](https://support.apple.com/HT204063)

:::warning

Note that after you remove OpenCore, your Mac will no longer boot and show the "prohibited" symbol. Be prepared to have a bootable USB drive with either OpenCore or natively-supported version of macOS before you uninstall the bootloader.

* This does not apply to native Macs just using OpenCore to achieve features like AirPlay to Mac and Sidecar, but it is still recommended to reinstall macOS after removing OpenCore, if using SMBIOS spoofing to enable Universal Control and other features.
:::



