pkgname=mingw32-lcms2
pkgver=2.3
pkgrel=3
pkgdesc="Small-footprint color management engine, version 2 (mingw32)"
arch=('any')
depends=('mingw32-runtime' 'mingw32-libtiff')
makedepends=('mingw32-gcc')
options=('!libtool' '!strip')
optdepends=('mingw32-libjpeg: JPEG support')
license=('MIT')
url="http://www.littlecms.com"
source=("http://downloads.sourceforge.net/sourceforge/lcms/lcms2-${pkgver}.tar.gz")
md5sums=('327348d67c979c88c2dec59a23a17d85')

build() {
  cd "${srcdir}/lcms2-${pkgver}"
  export CFLAGS="-O2 -mms-bitfields"
  export PKG_CONFIG_PATH="/usr/i486-mingw32/lib/pkgconfig/"
  unset LDFLAGS
  mkdir -p build && cd build
  ../configure \
      --prefix=/usr/i486-mingw32 \
      --host=i486-mingw32
  make
}

package() {
  cd "${srcdir}/lcms2-${pkgver}/build"
  make DESTDIR="${pkgdir}" install
  i486-mingw32-strip $pkgdir/usr/i486-mingw32/bin/*.exe
  i486-mingw32-strip -x $pkgdir/usr/i486-mingw32/bin/*.dll
  i486-mingw32-strip -g $pkgdir/usr/i486-mingw32/lib/*.a
  rm -rf "$pkgdir/usr/i486-mingw32/share"
}

# vim:set ts=2 sw=2 et:
