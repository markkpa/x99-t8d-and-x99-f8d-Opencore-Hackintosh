# x99-t8d-and-x99-f8d-Opencore-Hackintosh
For Huananzhi x99 Dual CPU Motherboards x99-t8d & x99-f8d - using Opencore 0.7.0 and Big Sur & RX570 Pulse 4GB graphics card.

Now includes AppleALC for REALTEK ALC887 (I no longer use VoodooHDA).  Also includes a customized slide value in boot args.  And includes my USB mapping.

I have a multiboot system including macos Big Sur, Windows 10, PopOS and Qubes.  I am NOT using opencore as a bootloader for Windows 10, PopOS and Qubes.  Therefore, I am no longer including the V3.EFI turbo boot unlock DXE driver in the opencore Drive folder.  Instead, I am injecting this driver directly into the bios using Shellx64.efi on a MSDOS formated USB called LOADV3 - files included.  I use .nsh script to automatically load the V3.EFI into FS0: (I have several scripts depending on where the USB is mounted (FS1-loadv3.nsh, FS2-loadv3.nsh, FS3-loadv3.nsh, FS7-loadv3.nsh).  Windows 10, PopOS & Qubes are much more stable being booted directly to the original bios rather than through opencore.  

Notes:  attached files are based on using modified x99-f8d bios (even though my motherboard is actually x99-t8d), microcode has been removed to support turbo-boost unlock on all cores.  The x99-f8d bios will work with x99-t8d motherboard using DDR3 memory.  However, you may want to remove onboard speaker as it makes loud sound on x99-t8d motherboard.  Also, x99-f8d bios will give faster performance on the x99-t8d motherboard - test scores will be better using x99-f8d bios even though memory timing features are missing.  To update bios, use Rufus in Windows to prepare bootable USB using FreeDOS; afterwards add 3 attached file:  9.bat, AFUDOS.exe and x99f8dL.rom.  Reboot in legacy mode to USB and execute 9.bat file.  I have included photos of my bios settings in "Bios_Settings.zip".  In my bios settings I have hyperthreading disabled as a personal preference as it improves single core performance.  However, hyperthreading enabled will work just fine.

Regarding Opencore, obviously, the EFI file excludes my Serial Number, MLB, SmUUID & ROM - you must add your own before using the EFI.

My EFI is setup for FileVault encryption.  You will need to modify several settings if you do not wish to support FileVault (refer to https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)

My EFI is setup for Opencore's GUI interface.  You will need to modify serveral settings if you do not wish to use Opencore's GUI (refer to https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html).  I have Misc --> HideAuxillary set to True to hide the Nvram-Reset feature (very dangerous to use).  Instead of Nvram-Reset, I use LauncherOption set to Full.  When you make changes, boot directly into your USB to overwrite the older OpenCore bootloader - this way you create a new OpenCore bootloader from the changes you saved to your USB (I suggest rebooting one time after creating a new OpenCore bootloader - before you use the new bootloader).

Turbo Boost Unlock for dual E5-2678v3 Xeon.  You must use modified bios with microcode removed AND under Kernel -> Quirks you must set AppleXcpmForceBoost to "True" (this is already setup correctly in my EFI).

Good Luck!

4/1/2021 - added power management patch - as per following reference:  https://github.com/Cclown98/X79-X99-X299-OPENCORE-EFI-CATALINA-BIGSUR

4/10/2021 - added futher power management with CPUFriendDataProvider.kext per following reference:  https://github.com/fewtarius/CPUFriendFriend
