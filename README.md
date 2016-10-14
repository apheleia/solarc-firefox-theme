# SolArc Firefox Theme
The SolArc version of this theem is still a work in progress and is only a preview.

Offical [SolArc](https://github.com/apheleia/solarc-theme) Firefox theme.

SolArc is a fork of the Arc theme: https://github.com/horst3180/arc-firefox-theme

### Requirements
This theme is compatible with Firefox 40+ and Firefox 38 ESR

**Note**: This theme is meant to be used in conjunction with the [SolArc GTK theme](https://github.com/apheleia/solarc-theme), don't use it with other GTK themes or it will look broken.

#### Manual building and installation

These instructions are for testers and package maintainers. They also allow to install the theme globally for all users.

You will need `autoconf` and `automake` for the following.

Clone the repository

    git clone https://github.com/horst3180/arc-firefox-theme && cd arc-firefox-theme

Generate the .xpi files (drag and drop these into your Firefox window)

    ./autogen.sh --prefix=/usr
    make mkxpi

Alternatively the theme can be installed globally without using the .xpi files

    ./autogen.sh --prefix=/usr
    sudo make install

Other build options to append to `autogen.sh` are

    --disable-light         disable Arc Light Firefox support
    --disable-darker        disable Arc Darker Firefox support
    --disable-dark          disable Arc Dark Firefox support

Uninstall the theme with

    sudo make uninstall
