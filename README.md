# st-arch

Personalized Arch Linux package configuration for [suckless](https://suckless.org)' [`simple terminal (st)`](https://st.suckless.org/).

## Applied Patches

### Official

The following offical patches from [st.suckless.org/patches](https://st.suckless.org/patches/) were applied.

- [solarized](https://st.suckless.org/patches/solarized/)
  - `st-no_bold_colors`
  - `st-solarized-dark`
- [boxdraw](https://st.suckless.org/patches/boxdraw/)
- [anysize](https://st.suckless.org/patches/anysize/)

## Custom

Additional information as to how additionally applied, custom patches were generated.

### `st-monospace-font`

This patch assigns the `monospace-11` font as default font. This works best if a `monospace` font is properly configured via [fontconfig](https://www.freedesktop.org/wiki/Software/fontconfig/) beforehand.

#### Generation

Clone the `st` repo

    git clone http://git.suckless.org/st
    cd st

Change font in `config.def.h` to `monospace-11`

    static char *font = "monospace-11";

Generate patch

    git diff > st-monospace-font-YYYYMMDD-RELEASE.diff

## Update sha256 sums

    makepkg -g >> PKGBUILD

## See also

- [How to build and install st (suckless simple terminal) from source on Arch Linux](https://brianbuccola.com/how-to-build-and-install-st-suckless-simple-terminal-from-source-on-arch-linux/)
- [diff generation](https://suckless.org/hacking/)
- [Getting solarized colors right with urxvt, st, tmux and vim](https://bbs.archlinux.org/viewtopic.php?id=164108)
