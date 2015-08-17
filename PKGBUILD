# Contributor: Laurent Laffont <laurent.laffont@gmail.com>


pkgname=phratch
pkgver=5.0
pkgrel=1
pkgdesc="Phratch is a programming language that makes it easy to create your own interactive stories, animations, games, music, and art — and share your creations on the web. Port of Scratch on Pharo."
arch=(i686 x86_64)
source=($pkgname-$pkgver.tar.gz)
url="http://www.phratch.com"
license=('MIT')
makedepends=('gendesk')
depends=('pharo-vm-latest')

source=('http://www.phratch.com/wp-content/uploads/2014/02/cropped-Robot-png-300x273.png')

md5sums=('0c98d2d5be58741c8d4efb51720252e9')

prepare() {
	gendesk -f --pkgname "$pkgname" --pkgdesc "$pkgdesc"
}


package() {
	cd $srcdir/
	wget -O Phratch.zip https://ci.inria.fr/pharo-contribution/view/Phratch/job/Phratch-OneClick/PHARO=4.0,PLATFORM=linux,VERSION=5.0,VM=vm/lastSuccessfulBuild/artifact/Phratch5.0-linux.zip
	mkdir -p $pkgdir/usr/share/phratch/
	unzip Phratch.zip -d $pkgdir/usr/share/phratch/

	mkdir -p $pkgdir/usr/bin/
	mkdir -p $pkgdir/usr/share/pixmaps/

	chgrp users $pkgdir/usr/share/phratch/Phratch/shared/Pharo4.0.changes
	chmod 775 $pkgdir/usr/share/phratch/Phratch/shared/Pharo4.0.changes

	ln -s /usr/share/phratch/Phratch/phratch $pkgdir/usr/bin/phratch

	cp $srcdir/cropped-Robot-png-300x273.png $pkgdir/usr/share/pixmaps/$pkgname.png
	install -Dm644 "$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
	install -D -m644 $srcdir/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop
}
