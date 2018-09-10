## Hive OS Drive Flashing Utility

![image 2018-04-25 16 42 29](https://user-images.githubusercontent.com/38013470/39249615-b4d10d6a-48a7-11e8-93b4-9598f4055b6b.jpg)


This is a bulk flashing utility which will help you to do 
headless and keyboardless migration to Hive of your farm.

You can find prebuild image here http://download.hiveos.farm/


### Step by Step Usage Instructions

- Download hive-flasher image from http://download.hiveos.farm/
- Download the latest Hive OS image
- Write hive-flasher.img to your Flash drive with Etcher (https://etcher.io/).
- After writing the image you will find HIVE-INSTALL disk partition with README.txt and other config files.
- Unpack Hive OS zip file to flash drive, hive-x.x-xx.img should be there after
- Use the following FARM_HASH or "RIG_ID autoincrement" to attach rig to your web account


### Using FARM_HASH

Go to your account on the web and find FARM_HASH value. 
Edit `hive-config.stub/rig-config-example.txt` to set FARM_HASH and RIG_PASSWD.
The rig will be created on the web after first run with the password specified.
RIG_ID will be autoassigned.


### Using RIG_ID autoincrement
> This method is obsolete and will be discontinued. FARM_HASH is much more convenient.

If you have created rigs sequentially on the web you can set starting RIG_ID in RIG_ID_SEQUENCE.txt file.
Or you can use this with a single id as well.
This value will be autoincremented after each flashing. 
You will be prompted to change it before flashing. 
Setting RIG_PASSWD is still required. FARM_HASH should be left blank.


### Flasher Config

There is a file `flasher-config.txt` with some settings of flasher.

`SHUTDOWN_AFTER_FLASHING=1` will shutdown rig after successful image writing.

`APPEND_STATIC_IP_TO_NAME=1`
If WORKER_NAME is set in `rig-config-example.txt` and Static IP is configured then IP will be appended to worker's name.
So WORKER_NAME is used as a prefix. 
Let's say WORKER_NAME is set to "rig" then if you have static network the name would become "rig-192.168.0.13".
 


### Manual actions

When you want to alter your password you can press Ctrl+C after boot to stop flashing.
Or press Esc after the first message.
Then maybe Alt+F2 to switch to other Linux terminal.
Run `mc` to find /mnt/hive-install/RIG_PASSWD.txt and edit it.
Then you can run `/hive-flasher/hive-flasher` again.



### Advanced. Custom flasher system build.

> This is just for fun, you don't have to do this 

You can make flasher image by yourself with the following steps.

- Create Ubuntu Server installation to SSD
- Put these files on disk
- Run `postinst`
- Put the latest Hive image to /mnt/hive-install (you'd better create NTFS partition)
- Put your starting rig id /mnt/hive-install/RIG_ID_SEQUENCE.txt and password into RIG_PASSWD.txt 
- Boot from this SSD on the rig leaving rig's drive in place
- After boot the script will detect rig's drive and hive flash image there with and precreate rig.conf
- ...
- PROFIT

