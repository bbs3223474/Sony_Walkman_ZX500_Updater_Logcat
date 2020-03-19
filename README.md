# Sony_Walkman_ZX500_Updater_Logcat
A record for Sony Walkman ZX500 Series internal updater engine's logcat and its public key file to verify the update payload.

This is a repo for recording the Sony Walkman ZX500 Series' updater engine logcat in order to research and find the way of
extracting the update zips from the device.
Right now, Sony never let users unlock its Walkman players and I had never found a way to extract the actual package from its
.UPG update files. But I noticed that the update zip was extracted to /data/ota_package/NW_WM_FW.zip. However, I can never 
access to the ota_package folder due to "permission denied" in adb console.

If there's a way to copy the update zips, then maybe there's a way to unlock or root this device.

Here's my research process:
 - New Walkman player will never be rooted by any software.
 - It's not using regular bootloader. It's using U-boot.
 - Hardware platform is NXP i.MX8 series.
 - Most of the folder cannot be accessed by adb shell commands.
 - /data/ ls "permission denied" but we can access the /data/local/tmp and copy files into it.
 - If using "adb reboot bootloader", it will enter the u-boot, but Windows will not install its driver correctly.
   If using Linux, the fastboot will recognize but both "fastboot oem unlock" and "fastboot flashing unlock" will not work,
   because this method requires confirmation on the device itself, but the Walkman shows nothing when inputing those commands.
 - The device uses AB partition.
