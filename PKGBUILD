# Maintainer: Benjamin Goldberg <jediben97@gmail.com>

pkgname=deezer-nativefier
pkgver=0.1.0
pkgrel=1
pkgdesc="A desktop app for Deezer created with nativefier"
arch=('x86_64')
depends=('c-ares' 'ffmpeg' 'gtk3' 'http-parser' 'libevent' 'libnghttp2'
         'libxslt' 'libxss' 'minizip' 'nss' 're2' 'snappy')
makedepends=('npm')
source=('package.json'
        'package-lock.json'
        'shortcuts.json'
        'deezer-nativefier.desktop')
sha256sums=('5a4b6a8c66c99b01fa350e52528be9ea33a14ce889ac7215eee330a35964ec9e'
            '509c67aededb4cc5a743ff85b8280ef0885d4f1bf3d29813fa09e64d55da5fb1'
            '5472ad4d0daebdbf4fdd6c21b37354df435f3ea19d3b28b6dab970ebf04f5bc7'
            'd309682d1daa31aa229fc3cddb1dc537a320383fce1db94f8d11770c599c8301')

build() {
    npm i
    npm run build
}

package() {
    desktop-file-install -m 644 --dir "$pkgdir/usr/share/applications/" "$srcdir/deezer-nativefier.desktop"
    cp -R "$srcdir/deezer-linux-x64" "$pkgdir/usr/share/$pkgname"
    install -D -m644 "$srcdir/deezer-linux-x64/resources/app/icon.png" "$pkgdir/usr/share/pixmaps/Deezer.png"
    mkdir -p "$pkgdir/usr/bin"
    ln -s "$pkgdir/usr/share/$pkgname/deezer" "$pkgdir/usr/bin/deezer-nativefier"
}