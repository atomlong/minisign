# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=minisign
pkgver=0.7
pkgrel=1
pkgdesc="A dead simple tool to sign files and verify digital signatures."
arch=('i686' 'x86_64')
url="https://github.com/jedisct1/minisign"
license=('custom:ISC')
depends=('libsodium')
makedepends=('cmake')
source=("$pkgname-$pkgver.tar.gz::https://github.com/jedisct1/minisign/archive/$pkgver.tar.gz")
sha512sums=('d23bab6d9c37132ccbc70209667e327704d24755d546504dc08c57b07177aeb8317ea8e1c54da5608d6f283cd7624228f9e932134f06a530ecb5eaf91390b7cc')

prepare() {
  mkdir -p build
}

build() {
  cd build

  cmake ../minisign-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release
  make
}

package() {
  make -C build DESTDIR="$pkgdir" install

  install -Dm644 minisign-$pkgver/LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
