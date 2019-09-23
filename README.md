# st

Arch Linux package configuration for [`st`](https://st.suckless.org/) with the following patches applied:

- [solarized](https://st.suckless.org/patches/solarized/)
  - `st-no_bold_colors`
  - `st-solarized-both`
- personalized patches
  - set the default font to `monospace-11`

## Personalized Patches

Descriptions regarding how personalized patches were generated

### `st-monospace-font`

Clone the `st` repo

    git clone http://git.suckless.org/st
    cd st

Change font in `config.def.h` to `monospace-11`

    static char *font = "monospace-11:antialias=true:autohint=true";

Generate patch

    git diff > st-monospace-font-YYYYMMDD-RELEASE.diff

## Update sha256 sums

    makepkg -g >> PKGBUILD

## See also

- [How to build and install st (suckless simple terminal) from source on Arch Linux](https://brianbuccola.com/how-to-build-and-install-st-suckless-simple-terminal-from-source-on-arch-linux/)
- [diff generation](https://suckless.org/hacking/)
- [Getting solarized colors right with urxvt, st, tmux and vim](https://bbs.archlinux.org/viewtopic.php?id=164108)
