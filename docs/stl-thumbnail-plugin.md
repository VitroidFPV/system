# Make STL thumbnails work in Dolphin

The [STL thumbnail thread](t3-thread://v1/a3aa3666-647d-41e9-9c76-1444ce673a33) found that the `stl-thumb-kde` RPM installed its Qt plugin under a Debian-style path. The user installed both RPMs. This machine now has the symlink below in Fedora's Qt plugin directory.

1. Build or obtain matching `stl-thumb` and `stl-thumb-kde` RPMs. The base RPM must provide `libstl_thumb.so()(64bit)` so DNF can resolve the KDE RPM's dependency. The thread fixed that RPM metadata in the `stl-thumb` project's `Cargo.toml`.
2. Install both RPMs in one transaction with `sudo dnf install ./PATH/TO/stl-thumb.rpm ./PATH/TO/stl-thumb-kde.rpm`.
3. Check whether the plugin exists at `/usr/lib64/qt6/plugins/kf6/thumbcreator/stlthumbnail.so`. If the RPM instead put it at the Debian-style path below, create the link:

   ```sh
   sudo mkdir -p /usr/lib64/qt6/plugins/kf6/thumbcreator
   sudo ln -s /usr/lib/x86_64-linux-gnu/qt6/plugins/kf6/thumbcreator/stlthumbnail.so \
     /usr/lib64/qt6/plugins/kf6/thumbcreator/stlthumbnail.so
   kbuildsycoca6
   ```

4. Reopen Dolphin. Enable **View → Show Previews**, check **Settings → Configure Dolphin → General → Previews** for **STL documents**, and open an STL file.

Use the link only while the RPM installs to the wrong path. A later package could install directly into Fedora's plugin directory; check the installed files first.
