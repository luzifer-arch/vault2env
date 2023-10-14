# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=vault2env
pkgver=2.2.2
pkgrel=1
pkgdesc="Small utility to transfer fields of a key in Vault into the environment"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('fa63e01336771de168097c056728ed6a7a1b7e1cd8263952b78d530bf0d975690df2e7082e1cb8070bea1577368ce9c0c431af63adf744ed6c2022a7f51dadde')

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
