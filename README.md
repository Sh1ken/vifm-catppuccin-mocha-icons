# Catppuccin Mocha + icons for vifm

A [vifm](https://vifm.info) color scheme with the [Catppuccin](https://catppuccin.com) Mocha palette and Nerd Font file icons, in one file.

- Bars, borders and the command line sit on the terminal background, so there are no grey bars and terminal transparency shows through.
- Directories, executables, links, archives, images, audio, video, documents and text files each get their own Mocha color.
- About 300 file icons, converted from [yazi](https://yazi-rs.github.io)'s built-in theme: exact names first (`.gitignore`, `Dockerfile`, …), then folder names, extensions and file types.

## Install

```sh
mkdir -p ~/.config/vifm/colors
curl -fLo ~/.config/vifm/colors/catppuccin-mocha-icons.vifm \
  https://raw.githubusercontent.com/Sh1ken/vifm-catppuccin-mocha-icons/main/colors/catppuccin-mocha-icons.vifm
```

Then in `~/.config/vifm/vifmrc`:

```vim
colorscheme catppuccin-mocha-icons Default-256 Default
```

vifm uses the first scheme in that list the terminal supports.

## Requirements

- A [Nerd Font](https://www.nerdfonts.com) v3 in your terminal, for the icons.
- For exact colors, a direct-color `$TERM`. vifm only uses the `gui*` (24-bit) colors when the terminfo entry supports them; otherwise it falls back to the nearest 256 colors. A zsh wrapper that switches when the terminal supports truecolor:

  ```zsh
  vifm() {
    if [[ $COLORTERM == (truecolor|24bit) ]]; then
      TERM=xterm-direct command vifm "$@"
    else
      command vifm "$@"
    fi
  }
  ```

  macOS's built-in ncurses lacks `xterm-direct`; Homebrew's `ncurses` provides it.

## Notes

The icons are set through vifm's `classify` option inside the color scheme. Switching to another color scheme replaces the colors but keeps the icons until you restart vifm or set `classify` yourself.

## License

MIT, see [LICENSE](LICENSE). The palette comes from Catppuccin and the icon mapping from yazi, both MIT.
