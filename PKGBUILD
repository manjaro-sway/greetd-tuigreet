# Maintainer: Antoine POPINEAU <antoine at popineau dot eu>

pkgname=greetd-tuigreet
pkgver=0.8.0
pkgrel=1

pkgdesc='A console UI greeter for greetd'
url='https://github.com/apognu/tuigreet'
license=(GPL3)
conflicts=(greetd-tuigreet-bin greetd-tuigreet-git)

arch=('x86_64' 'aarch64')

makedepends=(rust scdoc)

source=("tuigreet-${pkgver}.tar.gz::${url}/archive/${pkgver}.tar.gz"
  'tuigreet.conf')
sha256sums=('ed371ebe288a3e5782f01681c6c4ed4786b470184af286fa0e7b8898e47c154e'
  '8f83aee7874aab5d06981a1d1cd05df906368a79dbca90d157a33a2f023b67d3')

build() {
  cd "tuigreet-${pkgver}"

  cargo build --release
  scdoc <contrib/man/tuigreet-1.scd >contrib/man/tuigreet-1.roff
}

package() {
  depends=(gcc-libs)

  install -Dm755 "${srcdir}/tuigreet-${pkgver}/target/release/tuigreet" "${pkgdir}/usr/bin/tuigreet"
  install -Dm755 "${srcdir}/tuigreet-${pkgver}/contrib/man/tuigreet-1.roff" "${pkgdir}/usr/share/man/man1/tuigreet.1"
  install -Dm644 "${srcdir}/tuigreet-${pkgver}/LICENSE" "${pkgdir}/usr/share/licenses/tuigreet/LICENSE"

  install -Dm644 "${srcdir}/tuigreet.conf" "${pkgdir}/usr/lib/tmpfiles.d/tuigreet.conf"
}
