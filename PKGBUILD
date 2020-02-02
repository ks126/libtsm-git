# Maintainer: ks126 <ks126@outlook.jp>
pkgname=libtsm-git
_gitname=libtsm
pkgver=3.r18.g86aaa3e
pkgrel=1
pkgdesc="Terminal-emulator State Machine"
arch=('i686' 'x86_64')
url="https://github.com/ks126/libtsm"
license=('MIT')
depends=(glibc)
makedepends=('git' 'libxkbcommon')
provides=('libtsm')
conflicts=('libtsm')
options=(!libtool)
source=('git://github.com/ks126/libtsm')
sha256sums=('SKIP')

pkgver() {
  cd "$_gitname"
  git describe --long | sed -r "s/^$_gitname-//;s/([^-]*-g)/r\\1/;s/-/./g"
}

prepare() {
  cd "$srcdir/$_gitname"

  test -f ./configure || NOCONFIGURE=1 ./autogen.sh
  ./configure --prefix=/usr
}

build() {
  cd "$srcdir/$_gitname"

  make
}

package() {
  cd "$srcdir/$_gitname"
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$_gitname/COPYING"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
