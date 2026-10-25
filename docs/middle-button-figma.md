# Make middle-button dragging work in Figma

The [Figma thread](t3-thread://v1/cbf3e47d-1825-419b-b03f-23f7c2ad78ba) identified KDE button scrolling as the behavior that took the middle-button drag. The user confirmed that setting was disabled. The later middle-click paste changes were discussed, but the thread did not confirm their final state.

1. In KDE Plasma, open **System Settings → Mouse & Touchpad → Mouse → Scrolling**. Turn off **Press middle button and move mouse to scroll**.
2. In Zen, open `about:config` and set `middlemouse.paste` to `false` if middle-click still pastes into Figma.
3. On a Plasma Wayland session, the desktop-wide paste option is under **System Settings → Workspace Behavior → General Behavior → Middle Click: Pastes selected text**. Turn it off if you also want to stop paste in other apps.
4. Reload Figma and test middle-button dragging on the canvas.

The desktop-wide paste option can differ on X11. Do the browser setting separately when needed.
