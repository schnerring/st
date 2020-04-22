# Maintainer: Michael Schnerring <3743342+schnerring@users.noreply.github.com>
# Contributor: Michael Schnerring <3743342+schnerring@users.noreply.github.com>

pkgname=st-schnerring
pkgver=0.8.2.r44.g72e3f6c
pkgrel=1
pkgdesc="Simple virtual terminal emulator for X. Patched with solarized and other personal stuff."
arch=('i686' 'x86_64')
url='http://st.suckless.org/'
license=('MIT')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
provides=("st")
conflicts=("st")

_patches=('https://st.suckless.org/patches/solarized/st-no_bold_colors-20170623-b331da5.diff'
          'https://st.suckless.org/patches/solarized/st-solarized-dark-20180411-041912a.diff'
		  'https://st.suckless.org/patches/boxdraw/st-boxdraw_v2-0.8.2.diff'
		  'https://st.suckless.org/patches/anysize/st-anysize-0.8.1.diff'
		  'local://st-monospace-font-20190924-0.8.2.diff')

source=('git://git.suckless.org/st'
        "${_patches[@]}")

sha256sums=('SKIP'
            '71e1211189d9e11da93ee49388379c5f8469fcd3e1f48bb4d791ddaf161f5845'
            'b2d5e88a2616eafb82b2fefb63eecb0f9d71f839349ef40f9f69c1953444f88c'
            'c1b7ab7672815b73e8328ecc55300c12fddce9ecae4ab04ff4377bd9132089f6'
            '8118dbc50d2fe07ae10958c65366476d5992684a87a431f7ee772e27d5dee50f'
            '4da3b17e986ed9394d8056e6ced6b0a8d141a451be1f459c275817f2cd580651')

pkgver() {
    cd "${srcdir}/st"

    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd "${srcdir}/st"

	for patch in "${_patches[@]}"; do
		echo "Applying patch $(basename $patch)..."
		patch -Np1 < "$srcdir/$(basename $patch)"
	done
}

build() {
    cd "${srcdir}/st"

	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd "${srcdir}/st"

    make PREFIX=/usr DESTDIR="${pkgdir}" TERMINFO="/dev/null" install
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
}
