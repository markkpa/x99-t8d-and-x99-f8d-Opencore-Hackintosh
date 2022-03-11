Added alternate bios (x99f8dNa.rom) for stability when cores are more than 24 such as E5-2696v3 (-65mv, -60 cache, -60 sys).  For E5-2678v3 the standard bios (x99f8dN.rom) may give better performance.

For Huananzhi x99 Dual CPU Motherboards x99-t8d & x99-f8d - using Opencore 0.7.9 and Monterey 12.1 & RX570 Pulse 4GB graphics card.

I have a multiboot system including macos Monterey, Windows 10, Ubuntu.  I am NOT using opencore as a bootloader for Windows 10, Ubuntu - they are much more stable being booted directly to the original bios rather than through opencore (press F7 for bootloader).

Notes:  attached files are based on using modified x99-f8d bios (even though my motherboard is actually x99-t8d), bios has been modified to support turbo-boost unlock on all cores.  The x99-f8d bios will work with x99-t8d motherboard using DDR3 memory.  However, you may want to remove onboard speaker as it makes loud sound on x99-t8d motherboard.  To update bios, use Rufus in Windows to prepare bootable USB using FreeDOS; afterwards add 3 attached file:  9.bat, AFUDOS.exe and x99f8dN.rom.  Reboot in legacy mode to USB and execute 9.bat file.  I have included photos of my bios settings in "Bios_Settings.zip".  In my bios settings I have hyperthreading disabled as a personal preference as it improves single core performance.  However, hyperthreading enabled will work just fine.

Regarding Opencore, obviously, my EFI file excludes my Serial Number, MLB, SmUUID & ROM - you must add your own before using the EFI.

My EFI is setup for FileVault encryption.  You will need to modify several settings if you do not wish to support FileVault (refer to https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)

My EFI is setup for Opencore's GUI interface.  You will need to modify serveral settings if you do not wish to use Opencore's GUI (refer to https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html).  I have Misc --> HideAuxillary set to True to hide the Nvram-Reset feature (can be dangerous to use).  Instead of Nvram-Reset, I use LauncherOption set to Full.  When you make changes, boot directly into your USB to overwrite the older OpenCore bootloader - this way you create a new OpenCore bootloader from the changes you saved to your USB (I suggest rebooting one time after creating a new OpenCore bootloader - before you use the new bootloader).  If you have made many changes to the kext folder, it is often helpful to rebuild kextcache with "sudo kextcache -i /"

Turbo Boost Unlock for dual E5-xxxx v3 Xeon.  You must use modified bios AND under Kernel -> Quirks you must set AppleXcpmForceBoost to "True".

4/1/2021 - added power management patch - as per following reference:  https://github.com/Cclown98/X79-X99-X299-OPENCORE-EFI-CATALINA-BIGSUR

6/16/2021 - newest x99f8dN.rom bios has all the necessary modifications to support turbo-boot unlock for dual E5-xxxx-V3 CPU's, -75mv, -50 cache, -50 sys agent.  Thanks to https://github.com/Koshak1013/HuananzhiX99_BIOS_mods#Instructions-for-unlocking-the-maximum-frequency-for-all-cores-not-two-unlock and https://xeon-e5450.ru/socket-2011-3/e5-2600-v3/dobavlyaem-anlok-v-bios-raz-i-navsegda-cherez-s3turbotool/#_DXE

See Issues if you are trying to install earlier than Big Sur 11.3.  Also, see Issues if you are using a different graphics card than mine.
