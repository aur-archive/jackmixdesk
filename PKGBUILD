# Maintainer: speps <speps at aur dot archlinux dot org>

_ver=0.3-r4
pkgname=jackmixdesk
pkgver=0.3_r4
pkgrel=1
pkgdesc="An audio mixer for JACK with an OSC control interface and LASH support"
arch=(i686 x86_64)
url="http://sourceforge.net/projects/jackmixdesk/"
license=('GPL')
depends=('liblo' 'libidn' 'lash' 'jack')
makedepends=('phat')
install="$pkgname.install"
source=("http://downloads.sourceforge.net/project/$pkgname/$pkgname-$_ver.tar.gz"
        "$pkgname.desktop" "$pkgname.png")
md5sums=('d206a3d813bb37a94d86b6b5bbd8c92f'
         '6a6e291d8a25b1965e2cd96d8ab67f90'
         '76517265e70ed421513d9f4d5e608755')

build() {
  cd "$srcdir/$pkgname-$_ver"

  # enlarge string buffers (fix segfaults)
  sed -i '/gchar/s/10/30/' mixdesk_gtk.c

  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$_ver"
  make DESTDIR="$pkgdir/" install

  # desktop file
  install -Dm644 ../$pkgname.desktop \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  # icon
  install -Dm644 ../$pkgname.png \
    "$pkgdir/usr/share/pixmaps/$pkgname.png"
}

# vim:set ts=2 sw=2 et:
