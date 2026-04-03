![Audi A3 MHI2 RVC fillscreen backup camera](./_preview/Audi-MHI2-RVC-fullscreen_preview.jpg)

# Audi MHI2 RVC fullscreen (Audi-MHI2-RVC-fullscreen)
Audi MIB2 MMI (MHI2) rear-view camera modification for fullscreen stream display

Replace `displaymanager.json`, `.png` textures and `.kzb` assets to change video stream and  update GUI.

Full details: http://wiki.mib-helper.com/index.php?title=Audi_MHI2_RVC_fullscreen_patch

## Supported Vehicles ##
* Audi A3/S3/RS3 (8V) with MHI2 system running firmware `MHI2_ER_AU37x_P5089`.
* Need support for other cars and want to help develop the mod? Post stock files and display picture with stock config.

## Procedure
* download assets from this repository
* upload  assets to Audi MIB2 MMI unit
* reboot the unit
* check if it works and enjoy!

## Demo
https://www.youtube.com/watch?v=rX6YoU1oB2w

## Important
* Not for commecrial use - if you bought this, you got ripped off!
* Use at your own risk.
* Create backups before doing anything.
* Developed and tested with `MHI2_ER_AU37x_P5089`

## Guide
#### Connect to MIB2 (Terminal 1)
* `ssh -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 root@172.16.250.248` - connect with MIB2 at 172.16.250.248 IP address (D-Link Ethernet-to-USB adapter)
* `ssh -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 root@10.173.189.1` - connect with MIB2 at 10.173.189.1 IP address (WLAN hotspot)
* `4SapmKoq` - root password for MU1326
* `mount -uw /net/mmx/mnt/app && mount -uw /net/mmx/mnt/system` - enable write filesystem

#### Copy files from computer - WLAN hotspot (Terminal 2)
* `cd /location/to/Audi-MHI2-RVC-fullscreen/MH*/modification `
* A. `scp -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 -O .\displaymanager_8V0827566.json root@10.173.189.1:/mnt/system/etc/eso/production/displaymanager.json` - Copy displaymanager_8V0827566.json for A3 8V camera with 5Q0907441(A) module (pre facelift)
* B. `scp -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 -O .\displaymanager_8V0827566AB.json root@10.173.189.1:/mnt/system/etc/eso/production/displaymanager.json` - Copy displaymanager_8V0827566AB.json for A3 8V camera without additional module (facelift)
* C. `scp -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 -O .\displaymanager.json root@10.173.189.1:/mnt/system/etc/eso/production/` - Copy displaymanager_8V0827566AB.json for camera without additional module
* `scp -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 -O *.png root@10.173.189.1:/mnt/app/eso/hmi/lsd/images/HMIEarlyAppsEvoHighScale/` - Copy all png files
* `scp -oHostKeyAlgorithms=+ssh-rsa -oMACs=hmac-sha1 -O OPS_*.kzb root@10.173.189.1:/mnt/app/eso/hmi/lsd/kzbs/HMISystemEvoHighScale/` - Copy all kzb files

#### Finish MIB2 related changes (Terminal 1)
* `sync` - sync changes
* `mount -ur /net/mmx/mnt/app && mount -ur /net/mmx/mnt/system` - go back to read-only filesystem
* `exit` - log out from MIB

#### Reboot the MIB2 with the button combination
* `NAV/MAP` + `RADIO` + `Control Wheel`

## Too good to be free?
Coffee-powered development ☕ BuyCoffee → https://buycoffee.to/mrfix
