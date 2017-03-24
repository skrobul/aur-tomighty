# Maintainers:
# Slavi Pantaleev <s.pantaleev at gmail.com>
# Marek Skrobacki <skrobul@skrobul.com>

pkgname=tomighty
pkgver=0.7.2
pkgrel=1
pkgdesc='Desktop timer for Pomodoro Technique users'
arch=('any')
url="http://www.tomighty.org/"
license=('Apache')
depends=('java-runtime')
makedepends=('imagemagick maven')
source=('tomighty.sh'
		'tomighty.desktop'
		'git+https://github.com/tomighty/tomighty.git#branch=version-0.7'
		'https://github.com/ccidral/tomighty/raw/50d0094c024f1923bd0d6ff1bf77572ae5f5b5f6/img/tomato.ico')
md5sums=('941bdeb609169335cea3e9cf40904883'
		'66425a9e185788f720b466ca1caf5769'
		'SKIP'
		'f92eb060209cc142b9d6ff644f751b5f')

build() {
	cd $pkgname
	mvn clean package
}

package() {
	# This extracts several different sizes as {tomato}-{number}.png
	# tomato-0.png is the largest and the one we want
	convert $srcdir/tomato.ico $srcdir/tomato.png
	install -Dm 644 $srcdir/tomato-0.png $pkgdir/usr/share/pixmaps/$pkgname.png
	install -Dm 644 $srcdir/$pkgname/target/$pkgname-$pkgver.jar $pkgdir/usr/share/java/$pkgname/$pkgname.jar
	install -Dm 644 $pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop

	install -Dm 755 $pkgname.sh $pkgdir/usr/bin/$pkgname
}
