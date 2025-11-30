# discord-rolling

This is a rolling-release Arch Linux package for Discord. Whenever this package is installed with `makepkg -si`, it automatically downloads and installs whatever Discord's latest available tar.gz is.

This means that Discord can very quickly be updated by simply rebuilding this package. No need to mess with the PKGBUILD or manually install the tar.gz file.

I primarily made this due to issues I was experiencing with the Flatpak version of Discord due to its sandboxing. Because of these issues, I wanted to move over to using a native package, but discovered that there was no Discord package available for Artix, with it instead being stuck in Arch's Extra repo.

I would submit this to the AUR, but there is no way it would ever be accepted due to breaking various AUR guidelines by its nature, so I'll just host it here instead. Pretend this Git repository is an AUR package.
