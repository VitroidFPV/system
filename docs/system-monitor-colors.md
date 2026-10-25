# Keep System Monitor colors in sync

Plasma stores System Monitor sensor colors as literal values. This hook updates them after kde-material-you-colors changes the KDE accent color. The [script](../assets/update-systemmonitor-colors) came from the 21 September 2026 System Monitor session; its live test updated CPU and memory widgets.

1. Install `kreadconfig6`, a Qt 6 `qdbus` command, and kde-material-you-colors. On this Fedora machine the D-Bus command is `qdbus-qt6`.
2. Inspect a test System Monitor widget. Confirm that its type starts with `org.kde.plasma.systemmonitor` and that its `SensorColors` group has the keys you want to change. The script changes **all existing keys** in that group to one accent color.
3. Back up `~/.config/plasma-org.kde.plasma.desktop-appletsrc` and `~/.config/kde-material-you-colors/config.conf`.
4. Copy `assets/update-systemmonitor-colors` to `~/.local/bin/update-systemmonitor-colors` and make it executable:

   ```sh
   install -Dm755 assets/update-systemmonitor-colors ~/.local/bin/update-systemmonitor-colors
   ```

5. Set this key in the `[CUSTOM]` section of `~/.config/kde-material-you-colors/config.conf`:

   ```ini
   on_change_hook=~/.local/bin/update-systemmonitor-colors
   ```

6. Run `~/.local/bin/update-systemmonitor-colors`. Compare `kreadconfig6 --file kdeglobals --group 'Colors:Selection' --key BackgroundNormal` with the widget colors. The script prints how many colors it updated.

The hook needs the user's active Plasma D-Bus session. If it reports no widgets, inspect the widget types and groups on that system before changing the script.
