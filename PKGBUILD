pkgname=jdupes
pkgver=1.2.1
pkgrel=1
pkgdesc="A powerful duplicate file finder and an enhanced fork of 'fdupes'. "
arch=('x86_64')
url="https://github.com/jbruchon/jdupes"
license=('MIT')
source=(${pkgname}-${pkgver}.tar.gz::"https://github.com/jbruchon/${pkgname}/archive/v${pkgver}.tar.gz"
                "LICENSE")
sha512sums=('974b3b12e2bc8078ac4e48d4f7aec53292102c34e36bfbc1ecd1e83dd9e99f464e0d5ce95ccbd64bf99086f6a73a064da346a59933283fa86a561182b38b92cb'
            '7505b5a16fa21ba435829a6b470dc587554adf274930d50828900c25b19109b36fc4716ff4960a0cbeaf60c4f6ca096b164c891340a4bcb51f4d2b778b9267b6')

prepare() {
        cd "${pkgname}-${pkgver}"
        sed -i 's#PREFIX = /usr/local#PREFIX = /usr#' Makefile
}

build() {
        cd "${pkgname}-${pkgver}"
        make
}

package() {
        cd "${pkgname}-${pkgver}"
        ls -A ../
        read
        make DESTDIR="${pkgdir}/" install
        install -D -m644 "../LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
