# $Id: PKGBUILD 101156 2013-11-18 15:46:40Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>

pkgname=ejabberd-mod_archive
pkgver=20131111
pkgrel=1
pkgdesc="ejabberd message archive module"
arch=(any)
url="http://www.ejabberd.im/mod_archive"
license=('GPL')
depends=('ejabberd')
makedepends=('git')
options=()
replaces=('ejabberd-mod_archive-svn')
source=("git://github.com/processone/ejabberd-contrib.git"
	"build-fix.patch")
md5sums=('SKIP'
         '07fb25d3dbfa619ec12bc343d722b71f')

prepare() {
  cd $srcdir/ejabberd-contrib
  patch -p1 <$srcdir/build-fix.patch
}

build() {
  cd $srcdir/ejabberd-contrib/mod_archive
  ./build.sh
}

package() {
  cd $srcdir/ejabberd-contrib/mod_archive
  install -d -m 0755 $pkgdir/usr/lib/ejabberd
  cp -r ebin $pkgdir/usr/lib/ejabberd/ebin
  install -d -m0755 $pkgdir/usr/share/ejabberd-mod_archive
  cp -r src/*.sql $pkgdir/usr/share/ejabberd-mod_archive/
}
