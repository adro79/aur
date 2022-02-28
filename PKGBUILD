# Maintainer: Caleb Maclennan <caleb@alerque.com>
# Maintainer: Guillaume Horel <guillaume.horel@gmail.com>

pkgname=python-ufo2ft
_pyname=${pkgname#python-}
pkgver=2.25.3
pkgrel=1
pkgdesc='A bridge from UFOs to FontTools objects'
arch=(any)
url="https://github.com/googlefonts/$_pyname"
license=(MIT)
_pydeps=(booleanoperations
         cffsubr
         cu2qu
         defcon
         fonttools
         fs) # for fonttools[ufo]
depends=(python
         "${_pydeps[@]/#/python-}")
makedepends=(python-{build,installer}
             python-setuptools-scm
             python-wheel)
checkdepends=(python-compreffor
              python-pytest
              python-skia-pathops)
optdepends=(python-compreffor
            'python-lxml: enables faster UFO parsing'
            python-skia-pathops)
_archive="$_pyname-$pkgver"
source=("https://files.pythonhosted.org/packages/source/${_pyname::1}/$_pyname/$_archive.tar.gz")
sha256sums=('e0eb84a25f98a2bbce78ae5b8f7dcfa3c57d283d2dadc81331709343e27babde')

build() {
	cd "$_archive"
	python -m build -wn
}

check() {
	cd "$_archive"
	PYTHONPATH=Lib pytest tests
}

package() {
	cd "$_archive"
	python -m installer -d "$pkgdir" dist/*.whl
	install -Dm0644 -t "$pkgdir/usr/share/licenses/$pkgname/" LICENSE
}
