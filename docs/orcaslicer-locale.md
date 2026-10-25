# Run OrcaSlicer with the available locale

The OrcaSlicer Flatpak failed with `locale::facet::_S_create_c_locale name not valid` because its runtime lacked the Czech locale requested by the session. The [OrcaSlicer thread](t3-thread://v1/351c889a-9797-46b7-aeaf-ccc3364b7401) applied a per-user override. The current override is `LC_ALL=en_US.UTF-8`; a successful user-side launch was not recorded.

1. Confirm `en_US.UTF-8` is present in the Flatpak runtime.
2. Set only this app's locale:

   ```sh
   flatpak override --user --env=LC_ALL=en_US.UTF-8 com.orcaslicer.OrcaSlicer
   flatpak run com.orcaslicer.OrcaSlicer
   ```

3. Check the saved setting with `flatpak override --user --show com.orcaslicer.OrcaSlicer`.

This makes OrcaSlicer's regional formats English. Remove the app override with `flatpak override --user --reset com.orcaslicer.OrcaSlicer` if Czech locale support is later installed.
