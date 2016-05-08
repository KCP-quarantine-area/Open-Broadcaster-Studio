pkgname=obs-studio-git
pkgver=0.14.1.r23.g8fdd041
pkgrel=1
pkgdesc="Free and open source software for video recording and live streaming."
arch=("x86_64")
url="https://github.com/jp9000/obs-studio"
license=("GPL2")
depends=("ffmpeg" "jansson" "libxinerama" "libxkbcommon"
         "qt5-x11extras" "curl" "hicolor-icon-theme" "jack")
makedepends=("cmake" "git" "libxcomposite" "x264")
source=("$pkgname::git+https://github.com/jp9000/obs-studio.git#branch=master")
md5sums=("SKIP")

pkgver() {
  cd $pkgname
  git describe --long --tags | sed -r "s/([^-]*-g)/r\1/;s/-/./g"
}

build() {
  cd $pkgname

  mkdir -p build; cd build

  cmake -DCMAKE_INSTALL_PREFIX=/usr \
	-DOBS_VERSION_OVERRIDE=$pkgver ..

  make
}

package() {
  cd $pkgname/build

  make install DESTDIR="$pkgdir"
}
