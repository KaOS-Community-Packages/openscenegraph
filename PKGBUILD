pkgname=openscenegraph
pkgver=3.6.5
pkgrel=1
pkgdesc='Open Source, high performance real-time graphics toolkit'
url='http://www.openscenegraph.org'
arch=('x86_64')
license=('custom:OSGPL')
depends=('giflib' 'jasper' 'librsvg' 'xine-lib' 'curl' 'pth')
makedepends=('cmake' 'libvncserver' 'qt5-base' 'ffmpeg' 'mesa')
optdepends=('libvncserver' 'gdal' 'openexr' 'qt5-base' 'ffmpeg')
source=(https://github.com/openscenegraph/OpenSceneGraph/archive/OpenSceneGraph-${pkgver}.tar.gz)
sha256sums=('aea196550f02974d6d09291c5d83b51ca6a03b3767e234a8c0e21322927d1e12')
sha512sums=('7002fa30a3bcf6551d2e1050b4ca75a3736013fd190e4f50953717406864da1952deb09f530bc8c5ddf6e4b90204baec7dbc283f497829846d46d561f66feb4b')

build() {
  mkdir -p OpenSceneGraph-OpenSceneGraph-${pkgver}/build
  cd OpenSceneGraph-OpenSceneGraph-${pkgver}/build
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_LIBDIR=lib \
  ..
  VERBOSE=1 make
}

package() {
  cd OpenSceneGraph-OpenSceneGraph-${pkgver}
  make -C build DESTDIR="${pkgdir}" install
  install -Dm 644 LICENSE.txt -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
