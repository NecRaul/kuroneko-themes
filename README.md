# kuroneko-themes

GRUB themes for personal use.

## Requirements

`dialog` package is optionally required if you run the script without any options.

## Usage

```Bash
sudo bash install.sh
    -t, --theme     theme variant(s)          [hide|cat|shirt]          (default is hide)
    -i, --icon      icon variant(s)           [white|color]             (default is white)
    -s, --screen    screen display variant(s) [1080p|2k|4k]             (default is 1080p)
    -r, --remove    Remove theme              [hide|cat|shirt]          (must add theme name option, default is hide)
    -g, --generate  do not install but generate theme into directory    (must add your directory)
    -b, --boot      install theme into '/boot/grub' or '/boot/grub2'
    -h, --help      Show this help
```

_If no options are used, a user interface `dialog` will show up instead_

### Examples

- Install Hide theme on 2k display device:

```sh
sudo bash install.sh -t hide -s 2k
```

- Install Hide theme into /boot/grub/themes:

```sh
sudo bash install.sh -b -t hide
```

- Uninstall Hide theme:

```sh
sudo bash install.sh -r -t hide
```

## Issues / tweaks

### Correcting display resolution

- On the grub screen, press `c` to enter the command line
- Enter `vbeinfo` or `videoinfo` to check available resolutions
- Open `/etc/default/grub`, and edit `GRUB_GFXMODE=[height]x[width]x32` to match your resolution
- Finally, run `grub-mkconfig -o /boot/grub/grub.cfg` to update your grub config

### Setting a custom background

- Make sure you have `imagemagick` installed, or at least something that provides `convert`
- Find the resolution of your display, and make sure your background matches the resolution
  - 1920x1080 >> 1080p
  - 2560x1440 >> 2k
  - 3840x2160 >> 4k
- Place your custom background inside the root of the project, and name it `background.jpg`
- Run the installer like normal, but with -s `[YOUR_RESOLUTION]` and -t `[THEME]` and -i `[ICON]`
  - Make sure to replace `[YOUR_RESOLUTION]` with your resolution and `[THEME]` with the theme
