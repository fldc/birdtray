# Maintainer: Jonathon Fernyhough <jonathon_at+manjaro dot+org>
# Contributor: Kr1ss <kr1ss.x#yandex#com>
# Contributor: Dmitry Valter <dvalter"protonmail"com>

_pkgbase=birdtray
pkgname=$_pkgbase-git
pkgver=r1213.adb2bcc
pkgrel=1
pkgdesc="Run Thunderbird with a system tray icon."
arch=('i686' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://github.com/fldc/birdtray"
license=('GPL-3.0')
depends=(qt5-svg qt5-x11extras)
optdepends=('qt5-translations: Support for translations')
makedepends=(cmake git qt5-tools)
conflicts=($_pkgbase)
provides=($_pkgbase)
source=("git+$url.git")
sha1sums=(SKIP)

pkgver() {
  cd "$srcdir/birdtray"
  echo "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

build() {
  mkdir -p build && cd build
  cmake ../$_pkgbase \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release
  make
}

package() {
  make -C build DESTDIR="$pkgdir" install
  install -Dm644 -t "$pkgdir/usr/share/doc/$_pkgbase/" $_pkgbase/README.md
}
