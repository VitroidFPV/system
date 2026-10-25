# Toggle midscroll with a shortcut

The [midscroll thread](t3-thread://v1/e5992a90-0513-439d-b956-1d2308be43aa) set up a password-free toggle for the system `midscroll.service`. This machine has a launcher and a `Ctrl+Alt+M` Plasma shortcut. The thread confirmed direct launcher tests but did not record a successful key-press test after logout.

1. Confirm `midscroll.service` exists and find `systemctl` with `command -v systemctl`.
2. Use `sudo visudo -f /etc/sudoers.d/midscroll-toggle` to allow only start and stop. Replace the user name and binary path:

   ```sudoers
   YOUR_USERNAME ALL=(root) NOPASSWD: /usr/bin/systemctl start midscroll.service, /usr/bin/systemctl stop midscroll.service
   ```

3. Save this as `~/.local/share/applications/net.local.sh.desktop`:

   ```ini
   [Desktop Entry]
   Type=Application
   Name=Toggle Midscroll
   Exec=sh -c "if systemctl is-active --quiet midscroll.service; then sudo -n /usr/bin/systemctl stop midscroll.service; else sudo -n /usr/bin/systemctl start midscroll.service; fi"
   NoDisplay=true
   StartupNotify=false
   X-KDE-GlobalAccel-CommandShortcut=true
   ```

4. Add the launcher as a Plasma custom shortcut and assign `Ctrl+Alt+M`. The current shortcut is stored under `[services][net.local.sh.desktop]` in `~/.config/kglobalshortcutsrc`.
5. Log out and back in so Plasma reloads the shortcut. Press it twice and check `systemctl is-active midscroll.service` after each press.

Keep `sudo -n` in the command. It fails without prompting if the sudoers rule does not match. Do not keep an older `pkexec` shortcut with the same key; that was the source of repeated prompts in the thread.
