# Maintainer: Jakub Nowak <jakub.jakub.nowak@gmail.com>
# Contributor: Balló György <ballogyor+arch at gmail dot com>
# Contributor: Geoffroy Carrier <geoffroy.carrier@koon.fr>
# Contributor: Dalius <dagis@takas.lt>


tar -czvf patches.tar.gz patches/


_pkgname=wmctrl
pkgname=wmctrl-mrqubo
pkgver=1.07
pkgrel=6.2
pkgdesc="Control your EWMH compliant window manager from command line"
url="http://tripie.sweb.cz/utils/wmctrl/"
arch=('x86_64')
license=('GPL')
depends=(glib2 libxmu)
source=(http://tripie.sweb.cz/utils/wmctrl/dist/$_pkgname-$pkgver.tar.gz
        http://archive.debian.org/debian/pool/main/w/wmctrl/${_pkgname}_$pkgver-7.debian.tar.gz
        patches.tar.gz)
sha512sums=('4c77ad1e204e8d444f682ad1d05c0993bcab9097ac6d4b6a944556ab85acbe713f549dbaf443cd4d1226a162ce7d46fbd209c92652e87fc8e609feee74907daa'
            '2e5663f485801b871b388895d4b1eba90ae43dc353cdb0d6af962a51c1c45ea457523cb6c58fce1004998cbd500f553881e49c28eca776d34517d563efd7bbea'
            'SKIP')
provides=(wmctrl)
conflicts=(wmctrl)


prepare() {
  cd "$srcdir/$_pkgname-$pkgver"
  { cd "$srcdir/debian/patches" && xargs -a series realpath; } | xargs -n1 -- patch -p1 -i
  { cd "$srcdir/patches" && xargs -a series realpath; } | xargs -n1 -- patch -p1 -i
}

build() {
  cd "$srcdir/$_pkgname-$pkgver"
  ./configure --bindir="$pkgdir/usr/bin" --mandir="$pkgdir/usr/share/man"
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  make install
}
