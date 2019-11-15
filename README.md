<<<<<<< HEAD Стенд для домашнего занятия "Файловые системы и LVM"   stands-03-lvm>>>>>>>


[root@lvm vagrant]# history
    1  grub2-mkconfig -o /boot/grub2/grub.cfg
    2  cd /boot ; for i in `ls initramfs-*img`; do dracut -v $i `echo $i|sed "s/initramfs-//g;
    3  s/.img//g"` --force; done
    4  nano /boot/grub2/grub.cfg
    5  cd ..
    6  ls
    7  nano /boot/grub2/grub.cfg
    8  vi /boot/grub2/grub.cfg
    9  reboot
   10  lblk
   11  lsblk
   12   lvremove /dev/VolGroup00/LogVol00
   13  cd ..
   14  lvremove /dev/VolGroup00/LogVol00
   ##### не получилось выключение ВМ из-за граба, выключил ее vagrant halt lvm
   
   15  shutdown -r now
   16  shutdown  now
   17  poweroff
   18  quit
   19  quit
   20  exit
   21  grub2-mkconfig -o /boot/grub2/grub.cfg
   22  cd /boot ; for i in `ls initramfs-*img`; do dracut -v $i `echo $i|sed "s/initramfs-//g;
   23  s/.img//g"` --force; done
   24  nano /etc/grub2/grub.cfg
   25  lsblk
   26  pvcreate /dev/sdc /dev/sdd
   27  vgcreate vg_var /dev/sdc /dev/sdd
   28   lvcreate -L 950M -m1 -n lv_var vg_var
   29  mkfs.ext4 /dev/vg_var/lv_var
   30  mount /dev/vg_var/lv_var /mnt
   31  cp -aR /var/* /mnt/
   32  mkdir /tmp/oldvar && mv /var/* /tmp/oldvar
   33  umount /mnt
   34  mount /dev/vg_var/lv_var /var
   35  echo "`blkid | grep var: | awk '{print $2}'` /var ext4 defaults 0 0" >> /etc/fstab
   36  reboot
   37  exit
   38   lvremove /dev/vg_root/lv_root
   39  vgremove /dev/vg_root
   40  successfully removed
   41  [root@lvm vagrant]#
   42  pvremove /dev/sdb
   43  pvremove /dev/sdb1
   44  lvcreate -n LogVol_Home -L 2G /dev/VolGroup00
   45  mkfs.xfs /dev/VolGroup00/LogVol_Home
   46  mount /dev/VolGroup00/LogVol_Home /mnt/
   47  cp -aR /home/* /mnt/
   48   rm -rf /home/*
   49  umount /mnt
   50  mount /dev/VolGroup00/LogVol_Home /home/
   51  echo "`blkid | grep Home | awk '{print $2}'` /home xfs defaults 0 0" >> /etc/fstab
   52  touch /home/file{1..20}                                      ### создали файл для проверки#################################
   53   lvcreate -L 100MB -s -n home_snap /dev/VolGroup00/LogVol_Home  #### создали снапшет.
   54   rm -f /home/file{11..20}                                       ## удалили файлы в исходной директории для проверки
   55  umount /home
   56   lvconvert --merge /dev/VolGroup00/home_snap                    ## восстановил файлы со снапшота.
   57  mount /home
   58  ls -la                                                           ## проверили файлы !!!
   59  ls -la /root/
   60  cat /root/.bash_history
   61  lsblk
   62  cat /root/.bash_history
   63  cp /root/.bash_history /root/lesson_history
   64  exit
   65  cp /root/.bash_history /tmp/lesson_history
   66  chown 777 /tmp/lesson_history
   67  exit
   68  chmod -R 771 /tmp/*
   69  ls /tmp/
   70  cat /tmp/lesson_history
   71  exit
   72  cat /root/.bash_history
   73  history
[root@lvm vagrant]#
