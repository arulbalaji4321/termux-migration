Follow below steps to migrate the setup of Termux from Device A to Device B

Step 1. Backup termux on device A and run below command one by one.

 - `cd /data/data/com.termux/files`
 - `tar -zcvf ./termux-backup_20211031.tar.gz home usr`
 - `mv ./termux-backup_20211031.tar.gz /storage/[Device A ID]/Android/data/com.termux/files/termux-backup_20211031.tar.gz`

Step 2. Restore the setup of Termux on Device B.

- Use a bluetooth keyboard to connect to the device B
- Open the termux app
- Grant the storage permission to the MicroSD card with command `termux-setup-storage`, and click "Allow"
- Go to the termux root folder with `cd /data/data/com.termux/files`
- Check the soft link target location with `ls -al ~/storage/external-1` to get the [Device B ID] 
- Copy the backup file to the termux root folder: `cp /storage/[Device B ID]/Android/data/com.termux/files/termux-backup_20211031.tar.gz .`
- Override the current home and usr folder with `tar -zxvf ./termux-backup.tar.gz home && tar -zxvf termux-backup.tar.gz usr`

Restart the Termux and see if all the setup are in place on device B.

Replace any script/soft link using the `/storage/[Device A ID]` to `/storage/[Device B ID]`
