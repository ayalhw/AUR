# Maintainer: Coelacanthus <coelacanthus@outlook.com>

pkgname=gomclauncher
pkgver=1.3.6
pkgrel=1
epoch=
pkgdesc='gml: A Minecraft Launcher'
arch=('x86_64' 'i386')
url='https://github.com/xmdhs/gomclauncher'
license=('MIT')
depends=('glibc')
makedepends=('go')
source=("$pkgname-$pkgver.tar.gz::https://github.com/xmdhs/gomclauncher/archive/v$pkgver.tar.gz"
        "https://raw.githubusercontent.com/xmdhs/gomclauncher/v$pkgver/LICENSE")

b2sums=('d5b585b5d8ca7e1a82cbdb918c2fce60d6da191565a25b20e54708f0aeddf68d7b6a98249bd9683fed0ba51d5b163fbad004ad34d70132ee810e0a5b043332f1'
        'c0f4f5d14632f9204183a7096221aa794a20c34319abbbe527d1ca8bd234b3e744e23b398a73da64837396128dba466f7cfa93787f7b33dc05e1b90f70f7d579')

prepare() {
	cd "$pkgname-$pkgver"
	mkdir -p build/
}

package() {
	cd "$pkgname-$pkgver"

	go build \
		-trimpath \
		-buildmode=pie \
		-mod=readonly \
		-modcacherw \
		-ldflags "-linkmode external -extldflags \"${LDFLAGS}\"" \
		-o build \
		.

	install -Dm755 build/gomclauncher "$pkgdir/usr/bin/gml"
	install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/gomclauncher/LICENSE"
}
