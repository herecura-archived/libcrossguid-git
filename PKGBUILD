# Maintainer: BlackEagle <ike DOT devolder AT gmail DOT com>
# Contributer: graysky <graysky AT archlinux DOT us>
# Contributer: Cedric Girard <girard.cedric@gmail.com>

pkgname=libcrossguid-git
_gitname=libcrossguid
epoch=1
pkgver=0.2.2.r0.g5b45cdd
pkgrel=1
pkgdesc="Lightweight cross platform C++ GUID/UUID library"
arch=('i686' 'x86_64')
url="https://github.com/graeme-hill/crossguid"
license=('MIT')
makedepends=('git' 'cmake')
provides=('libcrossguid')
conflicts=('libcrossguid')
source=("$_gitname::git+https://github.com/graeme-hill/crossguid.git")
sha512sums=('SKIP')

pkgver() {
    cd "$_gitname"
    git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd "$_gitname"

    cmake .
    make
}

check(){
    cd "$_gitname"
    ./xgtest
}

package() {
    cd "$_gitname"
    install -D -m644 libxg.a "${pkgdir}/usr/lib/libxg.a"
    install -D -m644 Guid.hpp "${pkgdir}/usr/include/Guid.hpp"
    install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

