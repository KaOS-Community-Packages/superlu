pkgname=superlu
pkgver=5.2.1
pkgrel=1
pkgdesc="Set of subroutines to solve a sparse linear system"
arch=('x86_64')
url="http://crd.lbl.gov/~xiaoye/SuperLU/"
license=('custom')
depends=('gcc-libs' 'lapack')
makedepends=('cmake')
source=(
    'http://crd-legacy.lbl.gov/~xiaoye/SuperLU/superlu_${pkgver}.tar.gz'
    'LICENSE'
)
md5sums=(
    '3a1a9bff20cb06b7d97c46d337504447'
    'f78e2ac527dbb50f53766475a9c542bd'
)

prepare() {
    cd "${srcdir}/SuperLU_${pkgver}"
    mkdir -p build
}

build() {
    cd "${srcdir}/SuperLU_${pkgver}/build"
    cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_SHARED_LIBS=true -DCMAKE_INSTALL_LIBDIR=lib
    make
}

check() {
    cd "${srcdir}/SuperLU_${pkgver}/build"
    make test
}

package() {
    cd "${srcdir}/SuperLU_${pkgver}/build"
    make DESTDIR="${pkgdir}/" install
    install -dm755 "${pkgdir}"/usr/share/licenses/superlu
    install -m644 ../../LICENSE "${pkgdir}"/usr/share/licenses/superlu

}
