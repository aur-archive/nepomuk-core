# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=nepomuk-core
pkgver=4.14.3
pkgrel=1
pkgdesc="Contains the central Nepomuk services like file indexing, file system monitoring, query, storage, client libraries"
url="https://projects.kde.org/projects/kde/kdelibs/nepomuk-core"
arch=('i686' 'x86_64')
license=('GPL' 'LGPL' 'FDL')
depends=('kdelibs' 'poppler-qt' 'taglib' 'ffmpeg' 'ebook-tools'
         'kdegraphics-mobipocket' 'shared-desktop-ontologies' 'baloo4')
makedepends=('cmake' 'automoc4' 'doxygen')
source=("http://download.kde.org/stable/${pkgver}/src/${pkgname}-${pkgver}.tar.xz")
sha1sums=('503eaa3f4386f0547af95aa6c4ad816b281ffd6e')

prepare() {
  mkdir build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DKDE4_BUILD_TESTS=OFF \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install

  # Fix the python shebang
  sed -i 's|#!/usr/bin/env python|#!/usr/bin/env python2|' \
    "${pkgdir}"/usr/bin/nepomuk-simpleresource-rcgen
}
