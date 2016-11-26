# Includind 'pressend' into ISO Kali Linux

## Download 

```sh
 # mkdir iso
 # mount -o loop kali.iso iso/
 # mkdir cpiso
 # rsync -Cravzp -H iso/ cpiso/
 # umount iso
```

New directory
 
```sh
 # mkdir dir && cd dir/
 # gzip -dc < ../cpiso/install/initrd.gz | cpio --extract --verbose --make-directories \
--preserve-modification-time --no-absolute-filenames
```

## Hack the initrd

+ Edit or replace 'preseed.cfg'

```sh
 # rm -f ../cpiso/install/initrd.gz
 # find . | cpio --dereference --create --format=newc --verbose | gzip --best > ../cpiso/install/initrd.gz
```
testar depois
```sh
 # rm -f ../cpiso/install/initrd.gz
 # find . | cpio --create --format=newc --verbose | gzip --best > ../cpiso/install/initrd.gz
```


# Fix md5sum's

```sh
 # cd  ../cpiso/
 # md5sum `find . -follow -type f` > md5sum.txt
 # cd ..
```
# Create new image

```sh
 # genisoimage -v -J -r -l -V "Dexter" -iso-level 4 -o /home/dxt/Downloads/test.iso \
-cache-inodes -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot \
-allow-limited-size -boot-load-size 4 -boot-info-table /home/dxt/Downloads/cpiso
```
-r -J -l -D -V "customCD" -iso-level 4 -o mysystemcd.iso \
-cache-inodes -b isolinux/isolinux.bin -c isolinux/boot.cat \
-no-emul-boot -allow-limited-size -boot-load-size 4 -boot-info-table iso/

# Testing

First you need to create an image of the hard disk. In my case I have chosen to
emulate a 10GB hard-disk, but this size could be changed to correspond to your
needs. Note that the file is created in qcow format, so that only the non-empty
sectors will be written in the file.

```sh
 $ qemu-img create -f qcow hda.img 10G
```

Then start the test.iso with QEMU and our new image as the HD.


```sh
 $ qemu-system-x86_64 -m 2G -machine q35 -cdrom test.iso -hda hda.img -boot d
```

qemu-system-x86_64 -m 2G \
-cdrom /home/dxt/Downloads/test.iso -hda /home/dxt/Downloads/hda.img -boot d

## References:
https://wiki.debian.org/DebianInstaller/Preseed/EditIso
https://www.gnu.org/software/cpio/manual/cpio.html#format
https://forums.kali.org/archive/index.php/t-18174.html
