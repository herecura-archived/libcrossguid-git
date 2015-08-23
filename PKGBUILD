# Maintainer: Cedric Girard <girard.cedric@gmail.com>

pkgname=libcrossguid-git
_gitname=libcrossguid
pkgver=20150803.8f399e8
pkgrel=1
pkgdesc="Lightweight cross platform C++ GUID/UUID library"
arch=('i686' 'x86_64')
url="https://github.com/graeme-hill/crossguid"
license=('MIT')
makedepends=('git')
provides=('libcrossguid')
conflicts=('libcrossguid')
source=("$_gitname::git+https://github.com/graeme-hill/crossguid.git")
md5sums=('SKIP')

pkgver() {
  cd libcrossguid
  git log -1 --date=short --format="%cd.%h" | tr -d '-'
}

build() {
  cd libcrossguid

  g++ -c guid.cpp -o guid.o $CXXFLAGS -std=c++11 -DGUID_LIBUUID
  ar rvs libcrossguid.a guid.o

  g++ -c test.cpp -o test.o $CXXFLAGS  -std=c++11
  g++ -c testmain.cpp -o testmain.o $CXXFLAGS
  g++ test.o guid.o testmain.o -o test $CXXFLAGS -luuid
  chmod +x test

}

check(){
  cd libcrossguid
  ./test
}

package() {
  cd libcrossguid
  install -D -m644 libcrossguid.a "${pkgdir}/usr/lib/libcrossguid.a"
  install -D -m644 guid.h "${pkgdir}/usr/include/guid.h"
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
