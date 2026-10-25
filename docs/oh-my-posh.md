# Use the custom Oh My Posh prompt

The 20 September 2026 prompt session migrated the theme to the newer schema and made an ANSI-background variant. This machine's Bash startup uses the ANSI variant. Both complete files are saved in [assets](../assets/).

1. Install Oh My Posh and a font that contains the glyphs used by the prompt.
2. Copy either [the original theme](../assets/ompTheme.omp.json) or [the ANSI variant](../assets/ompTheme-ansi.omp.json) to a stable path, for example `~/Documents/ompTheme-ansi.omp.json`.
3. Add this line to `~/.bashrc`, with the path you chose:

   ```sh
   eval "$(oh-my-posh init bash --config "$HOME/Documents/ompTheme-ansi.omp.json")"
   ```

4. Open a new shell and check that the prompt renders. The thread validated the theme JSON and rendering at the time.

The ANSI variant uses ANSI backgrounds with black segment text; the two arrows on the second row use visible accent colors. The original theme uses fixed hex colors.
