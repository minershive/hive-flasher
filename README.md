## Hive OS Drive Flashing Utility

![image 2018-04-25 16 42 29](https://user-images.githubusercontent.com/38013470/39249615-b4d10d6a-48a7-11e8-93b4-9598f4055b6b.jpg)


This is a bulk flashing utility which will help you to do 
headless and keyboardless migration to Hive on your farm.

You can find prebuild image here http://download.hiveos.farm/

Or you can make it yourself with the following steps.

- Create Ubuntu Server installation to SSD
- Put these files on disk
- Run `postinst`
- Put the latest Hive image to /hive-flasher
- Make a symlink like `ln -s hive-latest-0.5.xxx.img hive.img`
- Put your staring RIG_ID and and RIG_PASSWD in corresponding file in /hive-flasher/*.txt (assuming you have created them on the web)
- Boot from this SSD on the rig leaving rig's drive in place
- After boot the script will detect rig's drive and hive flash image there with and precreate rig.conf
- ...
- PROFIT

When you want to alter your password you can press Ctrl+C after boot to stop flashing.
Run `mc` ti find /hive-flasher/RIG_PASSWD.txt and edit it.
Then you can run `hive-flasher` again.

