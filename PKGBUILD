# Maintainer: Mihai Bişog <mihai.bisog at [gmail] d0t com>
pkgname=fmt
pkgver=3.0.1
pkgrel=1
pkgdesc="Open-source formatting library for C++."
arch=("i686" "x86_64")
url="http://fmtlib.net"
license=("BSD")
makedepends=("cmake")

source=("https://github.com/fmtlib/fmt/archive/$pkgver.tar.gz")
md5sums=(b2c97427a696182b013d2cc0a2f939fe)

build() {
    cd "$pkgname-$pkgver"
    mkdir -p build && cd build

    cmake -DCMAKE_BUILD_TYPE=Release  \
          -DCMAKE_INSTALL_PREFIX=/usr \
          -DFMT_DOC=OFF               \
          ..
    make
}

check() {
    cd "$pkgname-$pkgver/build"
    make test
}

package() {
    cd "$pkgname-$pkgver/build"
    make DESTDIR="$pkgdir" install
    install -D -m644 ../LICENSE.rst "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -D -m644 ../ChangeLog.rst "${pkgdir}/usr/share/doc/${pkgname}/ChangeLog.rst"
}