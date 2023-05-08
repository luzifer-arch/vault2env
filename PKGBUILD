# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=vault2env
pkgver=2.2.1
pkgrel=1
pkgdesc="Small utility to transfer fields of a key in Vault into the environment"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('f9e1e75ed436f2bf48b27726cdb1989963d7d8d220c626922ba642df73c7111469fe9286ee3a2ede6dcf56c70085b70abd0f37358b5b98fd985dfa47b39dabaf')

build() {
	cd "${srcdir}/${pkgname}-${pkgver}"
	GO111MODULE=on GOPATH="${srcdir}/go" go install \
		-a -v \
		-ldflags="-X main.version=${pkgver}" \
		-mod=readonly

	GO111MODULE=on GOPATH="${srcdir}/go" go clean -modcache
}

package() {
	install -Dm755 "${srcdir}/go/bin/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "${srcdir}/${pkgname}-${pkgver}/LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
