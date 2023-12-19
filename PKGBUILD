# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=vault2env
pkgver=2.3.1
pkgrel=1
pkgdesc="Small utility to transfer fields of a key in Vault into the environment"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('d87c1180fc3e1d2296b8fc911d2302caacf53fef9edcf905688566a9d38771dd3c2fa7df9e575fd1c18fd44d4d091a4da56f8e589550a4a666ae9a05a5a29c5e')

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
