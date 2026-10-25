# Install the custom Zed theme

The [theme thread](t3-thread://v1/91b024b6-2d76-4c15-b4f8-82e3e1baf7c2) updated the installed One Dark Pro Vitroid theme's syntax colors. The current full theme is saved as [one-dark-pro-vitroid.json](../assets/one-dark-pro-vitroid.json).

1. Copy the file to Zed's user theme directory:

   ```sh
   install -Dm644 assets/one-dark-pro-vitroid.json ~/.config/zed/themes/one-dark-pro-vitroid.json
   ```

2. Select **One Dark Pro Vitroid** in Zed's theme picker. Open code in a few languages to check the syntax colors.

The file is the current theme snapshot. It includes the local UI colors as well as the syntax colors changed in the thread.
