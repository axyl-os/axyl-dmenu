# Maintainer: Gabriel Matthews <axyl.os.linux@gmail.com>

pkgname=axyl-dmenu-git
pkgver=5.0.r1.f83128a
pkgrel=1
pkgdesc="Command/Application Launcher for Axyl OS"
arch=('x86_64')
url="https://github.com/axyl-os/axyl-dmenu-git"
license=('MIT')
depends=('sh' 'glibc' 'coreutils' 'libx11' 'libxinerama' 'libxft')
makedepends=('git')
provides=("${pkgname}")
options=(!strip !emptydirs)
source=(${pkgname}::"git+https://github.com/axyl-os/${pkgname}.git")
md5sums=('SKIP')

pkgver() {
    cd "${_pkgname}"
    printf "5.0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd "$pkgname"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd "$pkgname"
    mkdir -p ${pkgdir}/opt/${pkgname}
    cp -rf * ${pkgdir}/opt/${pkgname}
    make PREFIX=/usr DESTDIR="${pkgdir}" install
}
