# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=vault2env
pkgver=2.3.0
pkgrel=1
pkgdesc="Small utility to transfer fields of a key in Vault into the environment"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('f65cffacf837ed41e8d6dceb0a11b1052451c31859164074e8e3790b2cbfec6569a6bf0254e210bf7cfaf61a4b389572075e813a46494516356368d176c85f90')

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
