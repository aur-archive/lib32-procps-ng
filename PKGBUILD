# $Id: PKGBUILD 170098 2012-11-01 17:28:55Z bisson $
# Maintainer: Gaetan Bisson <bisson@archlinux.org>
# Contributor: Eric Bélanger <eric@archlinux.org>

pkgname=lib32-procps-ng
pkgver=3.3.9
pkgrel=1
pkgdesc='Utilities for monitoring your system and its processes (32-bit)'
url='http://sourceforge.net/projects/procps-ng/'
license=('GPL' 'LGPL')
arch=('x86_64')
depends=('procps-ng' 'lib32-glibc')
source=("http://downloads.sourceforge.net/project/procps-ng/Production/procps-ng-${pkgver}.tar.xz")
sha1sums=('088c77631745fc75ee41fc29c254a4069be4869a')

build() {
  cd "${srcdir}/procps-ng-${pkgver}"

  export CC='gcc -m32'
  ./configure --exec-prefix=/ \
              --prefix=/usr \
              --sysconfdir=/etc \
              --libdir=/usr/lib32 \
              --sbindir=/usr/bin \
              --without-ncurses
  make
}

package() {
  cd "${srcdir}/procps-ng-${pkgver}"
  
  make DESTDIR="${pkgdir}" install

  rm -r ${pkgdir}/bin
  rm -r ${pkgdir}/usr/{bin,include,share}
}
