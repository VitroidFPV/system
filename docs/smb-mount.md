# Mount the NAS for applications

Dolphin could open `smb://vitroidpc.local/v-nas/`, but some applications needed a filesystem path. The [SMB thread](t3-thread://v1/7f11fc46-8091-4083-a3a8-81d30181c0f0) confirmed a temporary mount worked. The current `/etc/fstab` contains the entry below, and `/mnt/v-nas` is mounted.

1. Install the CIFS mount helper if it is absent. Confirm the share name and your local IDs with `id -u` and `id -g`.
2. Test a temporary mount:

   ```sh
   sudo mkdir -p /mnt/v-nas
   sudo mount -t cifs //vitroidpc.local/v-nas /mnt/v-nas \
     -o username=YOUR_SMB_USERNAME,uid=$(id -u),gid=$(id -g)
   ```

3. Create `/etc/samba/v-nas.credentials` with root-only access. Put `username=...` and `password=...` on separate lines. Keep the password out of this repository.

   ```sh
   sudo install -m 600 -o root -g root /dev/null /etc/samba/v-nas.credentials
   sudoedit /etc/samba/v-nas.credentials
   ```

4. Add one line to `/etc/fstab`. Replace the host, share, mount point, credential path, and IDs for the new machine:

   ```fstab
   //vitroidpc.local/v-nas /mnt/v-nas cifs credentials=/etc/samba/v-nas.credentials,uid=1000,gid=1000,_netdev,nofail,x-systemd.automount 0 0
   ```

5. Unmount the test mount, reload systemd, and test the saved entry:

   ```sh
   sudo umount /mnt/v-nas
   sudo systemctl daemon-reload
   sudo mount /mnt/v-nas
   ls /mnt/v-nas
   ```

If applications still cannot save, check write access to the share itself.
