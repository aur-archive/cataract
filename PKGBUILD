# Maintainer: OS Hazard <oshazard+aur@gmail.com>
# Contributor: Bjorn Michelsen <bjorn@bmichelsen.no>
# Contributor: Laszlo Papp <djszapi@gmail.com>

pkgname=cataract
pkgver=1.1.0
pkgrel=3
pkgdesc="Simple static web photo gallery, designed to be clean and easily usable"
arch=('i686 x86_64')
url="http://cgg.bzatek.net/"
license=('GPL')
depends=('pkg-config' 'imagemagick' 'exiv2')
source=(http://cgg.bzatek.net/files/$pkgname-$pkgver.tar.bz2)
md5sums=('64213b03ac218d5f68748319a1dac81c')

build() {
  cd $srcdir/$pkgname-$pkgver
  ./configure --prefix=/usr

  IFS=$(echo -en "\n\b");
  for i in $(grep -lR "#include <glib" src/);
  do
    sed -i 's/#include <glib\/.*>/#include <glib\.h>/g' "$i";
  done;

  make || return 1
  make DESTDIR=$pkgdir install || return 1
}
