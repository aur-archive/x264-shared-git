# Maintainer: Richard "Nothing4You" Schwab <mail NOSPAM w.tf-w.tf>

# Found typos, bugs or other problems? Feel free to create a pull-request:
# https://github.com/Nothing4You/PKGBUILDs

### WARNING ###
#
# Please keep in mind that installing this package might break other packages
# which were built against the x264 version in the extra repository!
# You might have to rebuild those packages depending on x264!

pkgname=x264-shared-git
pkgver=0.r2525.40bb568
pkgrel=1
epoch=1
pkgdesc="free library for encoding H264/AVC video streams (git version)"
arch=('i686' 'x86_64')
url="http://www.videolan.org/developers/x264.html"
depends=('glibc')
makedepends=('git' 'yasm')
conflicts=('x264' 'libx264')
provides=('x264' 'libx264')
license=('GPL')
source=(x264-shared::git://git.videolan.org/x264.git)
sha512sums=(SKIP)

pkgver() {
  cd "$srcdir/${pkgname%-*}"
  printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/${pkgname%-*}"

  # add '--bit-depth=10' if you want 10 bit output
  ./configure \
    --prefix=/usr \
    --enable-shared \
    --enable-pic

  make
}

package() {
  cd "$srcdir/${pkgname%-*}"
  make DESTDIR="$pkgdir" install
}
