## Hive OS Drive Flashing Utility

![image 2018-04-25 16 42 29](https://user-images.githubusercontent.com/38013470/39249615-b4d10d6a-48a7-11e8-93b4-9598f4055b6b.jpg)


This is a bulk flashing utility which will help you to do 
headless and keyboardless migration to Hive on your farm.

You can find prebuild image here http://download.hiveos.farm/


### Manual actions

When you want to alter your password you can press Ctrl+C after boot to stop flashing.
Or press Esc after the first message.
Then maybe Alt+F2 to switch to other Linux terminal.
Run `mc` to find /mnt/hive-install/RIG_PASSWD.txt and edit it.
Then you can run `/hive-flasher/hive-flasher` again.



### Custom system build

Or you can make image yourself with the following steps.

- Create Ubuntu Server installation to SSD
- Put these files on disk
- Run `postinst`
- Put the latest Hive image to /mnt/hive-install (you'd better create NTFS partition)
- Put your starting rig id /mnt/hive-install/RIG_ID_SEQUENCE.txt and password into RIG_PASSWD.txt 
- Boot from this SSD on the rig leaving rig's drive in place
- After boot the script will detect rig's drive and hive flash image there with and precreate rig.conf
- ...
- PROFIT

