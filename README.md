# x99-t8d-and-x99-f8d-Opencore-Hackintosh
For Huananzhi x99 Dual CPU Motherboards x99-t8d & x99-f8d - using Opencore 0.6.6 and Big Sur.

Notes:  attached files are based on using modified x99-f8d bios which includes the "above 4g decoding" feature, also microcode has been removed to support turbo-boost unlock on all cores.  The x99-f8d bios will also work with x99-t8d motherboard using DDR3 memory.  However, you may want to remove onboard speaker as it makes loud sound on x99-t8d motherboard.  Also, x99-f8d bios will give faster performance on the x99-t8d motherboard - test scores will be better using x99-f8d bios even though memory timing features are missing.  To update bios, use Rufus in Windows to prepare bootable USB using FreeDOS; afterwards add 3 attached file:  9.bat, AFUDOS.exe and x99f8dK.bin.  Reboot in legacy mode to USB and execute 9.bat file.  I have included photos of my bios settings in the file "Bios_Settings.zip".

Regarding Opencore, obviously, the EFI file excludes my Serial Number, MLB, SmUUID & ROM - you must add your own before using the EFI.

My EFI is setup for FileVault encryption.  You will need to modify several settings if you do not wish to support FileVault (refer to https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)

My EFI is setup for Opencore's GUI interface.  You will need to modify serveral settings if you do not wish to support Opencore's GUI (refer to https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html)

Turbo Boost Unlock for dual E5-2678v3 Xeon.  My EFI includes extra driver V3.efi to support turbo boost unlock on all cores (3.3Ghz on all cores).  You must use modified bios with microcode removed AND under Kernel -> Quirks you must set AppleXcpmForceBoost to "True" (this is already setup correctly in my EFI).

Good Luck!
