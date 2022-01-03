# twrp_device_ulefone_Note_11P
This is the DT for Ulefone Not 11P MT6771 A11. Forked for test compiling online.
The major problem is about encrypt_decrypt mode Trustkernel. If you can look more about that with reference so click in the website.
Maybe you can see @ADeadTrousers DT for know better so search ADeadTrousers/twrp_device_Unihertz_Atom_LXL

Considerations: Since TeamWin can't do good updates to its repository and it's specific to qualcomm devices (obviously there's more development and developers involved - you can't complain because there's more stuff), still the size of the recovery partition or boot devices Mediatek basics are still small (32MB ~ 41MB). Other Mediatek devices with recognized Xiaomi-Redmi brands; Realme or Infinix already have the boot partition with sizes from 67 to 128MB.

But I still wonder why keep a lyric font file in \ramdisk\twres\fonts\DroidSansFallback.ttf folder with size of 3.7MB?!
This is because some files related to encryption and decryption have sizes from 1.8 to 2.6MB and cannot be placed directly in the DT. But compiling the TWRP and having the boot.img(TWRP) file you can unpack, remove or replace the DroidSansFallback.ttf source file with a smaller one, put the files related to encryption, repack again to img and then we have a smaller file that 32MB.
Finally you can install the img file on the partition and test.

Another option is to condition in DT the bootimage partition size to 41MB. However it is necessary to unpack the img and dance with the DroidSansFallback.ttf font file, repack and blablabla.
