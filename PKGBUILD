pkgname=openscenegraph
pkgver=3.4.0
pkgrel=1
pkgdesc="An Open Source, high performance real-time graphics toolkit"
arch=('x86_64')
license=('custom:OSGPL')
url="http://www.openscenegraph.org"
depends=('giflib' 'jasper' 'librsvg' 'xine-lib' 'curl' 'pth')
makedepends=('cmake' 'libvncserver' 'qt5-base' 'ffmpeg' 'mesa')
optdepends=('libvncserver' 'gdal' 'openexr' 'poppler-glib' 'qt5-base' 'ffmpeg')
source=("http://trac.openscenegraph.org/downloads/developer_releases/OpenSceneGraph-${pkgver}.zip"
        "openscenegraph-ffmpeg3.patch")
md5sums=('a5e762c64373a46932e444f6f7332496'
         'f32564a54e944da1798aafdfacf996a3')

prepare() {
  cd OpenSceneGraph-$pkgver
# Fix build with ffmpeg 3.0
  patch -p2 -i ../openscenegraph-ffmpeg3.patch
}

build() {
  cd OpenSceneGraph-$pkgver
  [ $NOEXTRACT -eq 1 ] || cmake . \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release
  make
}

package() {
  cd OpenSceneGraph-$pkgver
  make DESTDIR="$pkgdir" install
  install -D -m644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  [ -d "$pkgdir/usr/lib64" ] && mv "$pkgdir/usr/lib64" "$pkgdir/usr/lib" || true
}
