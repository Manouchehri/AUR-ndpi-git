# Maintainer: David Manouchehri <david.manouchehri@riseup.net>
# Contributor: M0Rf30

_gitname=ndpi
pkgname="${_gitname}-git"
_gitbranch=dev
_gitauthor=ntop
pkgver=1.7.r593.g2b0809f
pkgrel=1
pkgdesc="Open and Extensible GPLv3 Deep Packet Inspection Library"
arch=('i686' 'x86_64')
url="https://www.ntop.org/products/ndpi/"
license=('GPL3')
replaces=('ndpi')
conflicts=('ndpi')
source=("git://github.com/${_gitauthor}/${_gitname}#branch=${_gitbranch}")
sha512sums=('SKIP')
conflicts=("${_gitname}")
provides=("${_gitname}")
makedepends=('git')

pkgver() {
	cd "${srcdir}/${_gitname}"
	(
		set -o pipefail
		git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
}

build() {
	cd "${srcdir}/${_gitname}"
	./autogen.sh
	./configure --prefix=/usr
	make
}
		 
package() {
	cd "${srcdir}/${_gitname}"
	make DESTDIR="${pkgdir}" install
}
