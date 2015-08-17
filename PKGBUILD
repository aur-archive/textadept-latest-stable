# Maintainer: Ivan de Jesús Pompa García <ivan.pompa@gmx.com>

pkgname=textadept-latest-stable
pkgver=7.5
pkgrel=5
pkgdesc="A fast, minimalist, and ridiculously extensible cross-platform text editor. Package for GTK3."
arch=('i686' 'x86_64')
url="http://foicica.com/textadept"
license=('MIT')

depends=('gtk3'
		'lua'
		'desktop-file-utils')

conflicts=('textadept')
provides=('textadept')

source=(
	http://foicica.com/textadept/download/textadept_LATEST.i386.tgz
	textadept.desktop
	textadept.install
)

md5sums=(
	7471d0b513494ab02d8de2c95496ea68
	06e1a44d8160a0bba8305a83c7dc5fc6
	d586e0d8596b8b77a3cbe36463c02704
)

_arch='i386'

if [ "${CARCH}" == "x86_64" ]; then
	_arch='x86_64'

	source=(
		http://foicica.com/textadept/download/textadept_LATEST.x86_64.tgz
		textadept.desktop
		textadept.install
	)

	md5sums=(
		69fb1b1e7863436c557246a976067326
		06e1a44d8160a0bba8305a83c7dc5fc6
		d586e0d8596b8b77a3cbe36463c02704
	)
fi

#build() {
	#cp fix-for-mv-libs.patch ${srcdir}/textadept_${pkgver}.src/src
	#cd ${srcdir}/textadept_${pkgver}.src/src
	#patch -Np1 < fix-for-mv-libs.patch
	#cd ${srcdir}/textadept_${pkgver}.src/src
	#make GTK3=1 -e CXX="g++ -lgobject-2.0 -lgmodule-2.0 -llua -lm -ldl" textadept || return 1
  #make GTK3=1 -e CXX="g++ -fpermissive -lgmodule-2.0 -llua -lm -ldl" textadept-curses
#}

package() {
	if [ ! -d "${pkgdir}/usr/share/textadept" ]; then
		mkdir -p ${pkgdir}/usr/share/textadept
	fi

	if [ ! -d "${pkgdir}/usr/share/textadept" ]; then
		rm -rf ${pkgdir}/usr/share/doc/textadept
	fi

	cd ${srcdir}/textadept_${pkgver}.${_arch}
	cp -R -t ${pkgdir}/usr/share/textadept core init.lua lexers LICENSE \
		modules themes textadept textadept-curses textadeptjit textadeptjit-curses \
		properties.lua
	cp -R doc ${pkgdir}/usr/share/textadept

	install -D -m644 ${startdir}/textadept.desktop \
		${pkgdir}/usr/share/applications/${pkgname}.desktop
}

install=textadept.install
