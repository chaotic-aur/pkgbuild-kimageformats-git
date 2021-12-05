# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kimageformats-git
pkgver=_r369.g81603ed
pkgrel=1
pkgdesc='Image format plugins for Qt5'
arch=(x86_64)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(qt5-base)
makedepends=(extra-cmake-modules-git karchive-git libavif openexr libheif)
optdepends=('karchive: plugin for Krita and OpenRaster images'
            'libavif: AVIF format support'
            'openexr: EXR format support'
            'libheif: HEIF format support')
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(kf5-git)
source=("git+https://invent.kde.org/frameworks/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DKIMAGEFORMATS_HEIF=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
