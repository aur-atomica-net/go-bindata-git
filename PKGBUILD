# Maintainer: Mineko <minekorox@gmail.com>

_pkgname=go-bindata
pkgname=${_pkgname}-git
pkgver=v3.0.7.r72.ga0ff256
pkgrel=1
pkgdesc="Converts any file into managable Go source code - git checkout"
arch=('x86_64')
url="http://github.com/jteeuwen/go-bindata/"
license=('CC0-1.0')
makedepends=('git' 'go')
provides=('go-bindata')
conflicts=('go-bindata')
source=("git+https://github.com/jteeuwen/${_pkgname}.git")
sha256sums=('SKIP')

pkgver() {
cd "$srcdir/$_pkgname"
git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
# setup local gopath
mkdir -p $srcdir/src/github.com/jteeuwen
ln -s $srcdir/$_pkgname $srcdir/src/github.com/jteeuwen/$_pkgname
}

build() {
cd $srcdir/src/github.com/jteeuwen/$_pkgname/$_pkgname
GOPATH="$srcdir" go build
}

package() {
cd "$srcdir/$_pkgname"

install -Dm755 $_pkgname/$_pkgname $pkgdir/usr/bin/$_pkgname
}

# vim:set ts=2 sw=2 ft=sh et:
