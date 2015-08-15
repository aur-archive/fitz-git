# Maintainer: Adam Reichold <adamreichold@myopera.com>
pkgname=fitz-git
pkgver=20120613
pkgrel=1
pkgdesc='The MuPDF renderer. (development version)'
arch=('i686' 'x86_64')
url='http://mupdf.com'
license=('GPL3')
depends=('freetype2' 'libjpeg' 'openjpeg' 'jbig2dec')
makedepends=('git')
conflicts=('mupdf')
_gitroot="git://git.ghostscript.com/mupdf.git"
_gitname="mupdf"

build() {
  cd "$srcdir"

  msg 'Obtaining source code...'

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull $_gitroot
  else
    git clone --depth 1 $_gitroot && cd $_gitname
  fi

  msg 'Building program...'

  make build=release build/release/libfitz.a
}

package() {
  cd "$srcdir/$_gitname"

  install -Dm644 fitz/fitz.h $pkgdir/usr/include/fitz.h
  install -Dm644 fitz/memento.h $pkgdir/usr/include/memento.h
    
  install -Dm644 build/release/libfitz.a $pkgdir/usr/lib/libfitz.a
}
