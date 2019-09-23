# Maintainer: Michael Schnerring <3743342+schnerring@users.noreply.github.com>
# Contributor: Michael Schnerring <3743342+schnerring@users.noreply.github.com>

pkgname=st-schnerring
_pkgname=st
pkgver=0.8.2.14.g2b8333f
pkgrel=1
pkgdesc="Simple virtual terminal emulator for X. Patched with solarized and other personal stuff."
arch=('i686' 'x86_64')
url='http://st.suckless.org/'
license=('MIT')
depends=('libxft')
makedepends=('ncurses' 'git')
provides=("${_pkgname}")
conflicts=("${_pkgname}")
options=('zipman')

_patches=('https://st.suckless.org/patches/solarized/st-no_bold_colors-20170623-b331da5.diff'
          'https://st.suckless.org/patches/solarized/st-solarized-both-20190128-3be4cf1.diff')

source=('git://git.suckless.org/st'
        "${_patches[@]}")

sha256sums=('SKIP'
            '71e1211189d9e11da93ee49388379c5f8469fcd3e1f48bb4d791ddaf161f5845'
            '0f47385bef0795c859818d1b88ea826418e62a7b5022dcfe7910c4bab1393faf')

pkgver() {
	cd "${_pkgname}"
	git describe --tags | sed 's/-/./g'
}

prepare() {
	cd "$_pkgname"

	sed '/@tic/d' -i Makefile

	for patch in "${_patches[@]}"; do
		echo "Applying patch $(basename $patch)..."
		patch -Np1 -i "$srcdir/$(basename $patch)"
	done
}

build() {
	cd "$_pkgname"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "${_pkgname}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/${_pkgname}/README"
}
