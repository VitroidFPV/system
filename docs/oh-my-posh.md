# Use the custom Oh My Posh prompt

The 20 September 2026 prompt session migrated the theme to the newer schema and made an ANSI-background variant. This machine's Bash startup uses the ANSI variant. Both complete files are saved in [assets/configs](../assets/configs/).

1. Install Oh My Posh and a font that contains the glyphs used by the prompt.
2. Add this line to `~/.bashrc` to load [the ANSI variant](../assets/configs/ompTheme-ansi.omp.json) from the repository's `main` branch:

   ```sh
   eval "$(oh-my-posh init bash --config 'https://raw.githubusercontent.com/VitroidFPV/system/refs/heads/main/assets/configs/ompTheme-ansi.omp.json')"
   ```

3. Open a new shell and check that the prompt renders. Oh My Posh downloads and caches remote configs; an internet connection is needed when the cache is empty. The thread validated the theme JSON and rendering at the time.

The ANSI variant uses ANSI backgrounds with black segment text; the two arrows on the second row use visible accent colors. [The original theme](../assets/configs/ompTheme.omp.json) uses fixed hex colors.
