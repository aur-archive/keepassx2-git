# Maintainer: Lev Lybin <lev.lybin@gmail.com>
# Contributor: Alucryd <alucryd at gmail dot com>
# Contributor: Paolo Stivanin <admin at polslinux dot it>

pkgname=keepassx2-git
_gitname=keepassx
pkgver=2.0.alpha6
pkgrel=1
pkgdesc="KeePassX is a cross platform port of the windows application 'Keepass Password Safe'. It is an OpenSource password safe which helps you to manage your passwords in an easy and secure way. It uses a highly encrypted database locked with one master key."
arch=('i686' 'x86_64')
url="https://github.com/keepassx/keepassx"
license=('GPL2')
depends=('libxtst' 'qt4')
install=keepassx2.install
makedepends=('git' 'intltool' 'cmake')
conflicts=('keepassx-svn' 'keepassx')
source=('git+https://github.com/keepassx/keepassx.git')
md5sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd $_gitname
  cmake . -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_BINDIR=/usr/bin -DCMAKE_INSTALL_LIBDIR=/usr/lib -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_GUI_TESTS=ON
  make
}

package() {
  cd $_gitname
  make PREFIX=/usr DESTDIR="$pkgdir" install
}
