# Install the Lucide KDE icon theme

The [icon theme thread](t3-thread://v1/0de1b784-9658-41bc-945d-4e03a2c237be) led to the separate [Lucide KDE project](https://github.com/VitroidFPV/lucide-kde). The current machine has `~/.local/share/icons/Lucide-KDE/index.theme`; it inherits Breeze and sets `FollowsColorScheme=true`.

1. Get a release archive from the Lucide KDE project, or build the theme using that repository's instructions. Keep its included Lucide license notices.
2. Put the `Lucide-KDE` directory under `~/.local/share/icons/`. Check that `~/.local/share/icons/Lucide-KDE/index.theme` exists.
3. In KDE **System Settings → Colors & Themes → Icons**, select **Lucide KDE**.
4. Check tray icons on light and dark panels. Apps that supply their own image may not follow the icon theme.

The installed `index.theme` uses `Inherits=breeze` and `FollowsColorScheme=true`; preserve those settings when rebuilding the theme.
