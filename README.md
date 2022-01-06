# twrp_device_ulefone_Note_11P
This is the DT for Ulefone Note 11P MT6771 A11. Forked for test compiling online.
The major problem is about encrypt_decrypt mode Trustkernel. If you can look more about that with reference so click in the website.
Maybe you can see @ADeadTrousers DT for know better so search ADeadTrousers/twrp_device_Unihertz_Atom_LXL

Considerations: Since TeamWin can't do good updates to its repository and it's specific to qualcomm devices (obviously there's more development and developers involved - you can't complain because there's more stuff), still the size of the recovery partition or boot devices Mediatek basics are still small (32MB ~ 41MB). Other Mediatek devices with recognized Xiaomi-Redmi brands; Realme or Infinix already have the boot partition with sizes from 67 to 128MB.

But I still wonder why keep a lyric font file in \ramdisk\twres\fonts\DroidSansFallback.ttf folder with size of 3.7MB?!
This is because some files related to encryption and decryption have sizes from 1.8 to 2.6MB and cannot be placed directly in the DT. But compiling the TWRP and having the boot.img(TWRP) file you can unpack, remove or replace the DroidSansFallback.ttf source file with a smaller one, put the files related to encryption, repack again to img and then we have a smaller file that 32MB.
Finally you can install the img file on the partition and test.

Another option is to condition in DT the bootimage partition size to 41MB. However it is necessary to unpack the img and dance with the DroidSansFallback.ttf font file, repack and blablabla.


# TWRP device trees for Ulefone NOTE 11P - 8GB RAM - 128GB ROM
#Specs => https://www.devicespecifications.com/en/model/0ab45556

## Status --> ALPHA

Current state of features (from [here](https://twrp.me/faq/OfficialMaintainer.html)):

### Blocking checks

- [ ] Correct screen/recovery size
- [ ] Working Touch, screen
- [ ] Backup to internal/microSD
- [ ] Restore from internal/microSD
- [ ] reboot to system
- [ ] ADB

### Medium checks

- [ ] update.zip sideload
- [ ] UI colors (red/blue inversions)
- [ ] Screen goes off and on
- [ ] F2FS/EXT4 Support, exFAT/NTFS where supported
- [ ] all important partitions listed in mount/backup lists
- [ ] backup/restore to/from external (USB-OTG) storage (not supported by the device) (not tested)
- [ ] [backup/restore to/from adb](https://gerrit.omnirom.org/#/c/15943/)
- [ ] decrypt /data
- [ ] Correct date

### Minor checks

- [ ] MTP export
- [ ] reboot to bootloader
- [ ] reboot to recovery
- [ ] poweroff
- [ ] battery level
- [ ] temperature
- [ ] encrypted backups (no option, need to test)
- [ ] input devices via USB (USB-OTG) - keyboard, mouse and disks (not supported by the device) (not tested)
- [ ] USB mass storage export (not tested)
- [ ] set brightness
- [ ] vibrate (Doesn't work, WIP)
- [ ] screenshot
- [ ] partition SD card

## Building

```bash
source build/envsetup.sh
lunch twrp_NOTE_11P-eng
mka bootimage
```
