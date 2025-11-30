# Maintainer: OpenSauce <opensauce04@gmail.com>

# Based on discord-ptb AUR package:
#   Maintainer: Tim Schumacher <timschumi@gmx.de>
#   Contributor: Filipe Laíns (FFY00) <lains@archlinux.org>
#   Contributor: Morgan <morganamilo@archlinux.org>

pkgname=discord-rolling
_pkgname=Discord
installname=discord
pkgver=2025.11.30.21.00.07
pkgrel=1
pkgdesc="All-in-one voice and text chat for gamers - Rolling package"
arch=('x86_64')
url='https://discordapp.com'
license=('custom')
provides=(discord)
options=(!strip)
depends=('libnotify' 'libxss' 'nspr' 'nss' 'gtk3')
optdepends=('libpulse: Pulseaudio support'
            'xdg-utils: Open files'
            'noto-fonts-cjk: Font for special characters such as /shrug face'
            'emoji-font: Fonts for emoji support')
source=("discord-$pkgver.tar.gz::https://discord.com/api/download?platform=linux&format=tar.gz"
        'LICENSE.html::https://discordapp.com/terms'
        'OSS-LICENSES.html::https://discordapp.com/licenses')
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

pkgver() {
  date +%Y.%m.%d.%H.%M.%S
}

prepare() {
  cd $_pkgname
  sed -i "s|Exec=.*|Exec=/usr/bin/$installname|" $installname.desktop
  echo 'Path=/usr/bin' >> $installname.desktop
}

package() {
  install -d "$pkgdir"/opt/$installname
  cp -a $_pkgname/. "$pkgdir"/opt/$installname

  chmod 755 "$pkgdir"/opt/$installname/$_pkgname

  rm "$pkgdir"/opt/$installname/postinst.sh

  install -d "$pkgdir"/usr/{bin,share/{pixmaps,applications}}
  ln -s /opt/$installname/$_pkgname "$pkgdir"/usr/bin/$installname
  ln -s /opt/$installname/discord.png "$pkgdir"/usr/share/pixmaps/$installname.png
  ln -s /opt/$installname/$installname.desktop "$pkgdir"/usr/share/applications/$installname.desktop

  # setuid on chrome-sandbox
  chmod u+s "$pkgdir"/opt/$installname/chrome-sandbox

  install -Dm644 LICENSE.html "$pkgdir"/usr/share/licenses/$installname/LICENSE.html
  install -Dm644 OSS-LICENSES.html "$pkgdir"/usr/share/licenses/$installname/OSS-LICENSES.html
}
