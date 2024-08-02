# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Frederik Schwan <freswa at archlinux dot org>
# Contributor: Hao Long <imlonghao@archlinuxcn.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python"
_pkg="aioetherscan"
pkgbase="${_py}-${_pkg}"
pkgname=(
  "${pkgbase}"
)
pkgver=0.9.4
pkgrel=1
_pkgdesc=(
  'Etherscan API async Python wrapper.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_ns="ape364"
_http="https://github.com"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=3.9"
  "${_py}-aiohttp>=3.4"
  "${_py}-asyncio_throttle>=1.0.1"
  "${_py}-aiohttp-retry>=2.8.3"
)
makedepends=(
  "${_py}-"{build,installer,poetry-core,wheel}
)
checkdepends=(
  "${_py}-pytest>=8.2.2"
  "${_py}-pytest-asyncio>=0.23.7"
)
provides=(
  "${_pkg}=${pkgver}"
)
conflicts=(
  "${_pkg}"
)
_commit="02ba4ddd1da12bbc86ed462e6f3a9f0d171b1678"
source=(
  "${url}/archive/${_commit}.zip"
  # Release tarball - never released one
  # "${url}/archive/v${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
b2sums=(
  '044b69d3e38e50012dbe3253477af7e8649d2cae3993646a6e4ad12900c0e69fc90cb4b9b13b56daea9783a1869a855aaeee9dd260ee0cefb11c0ce76d446430'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  python \
    -m \
      build \
    --wheel \
    --no-isolation
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
      --destdir="${pkgdir}" \
      dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE
}

# vim:set sw=2 sts=-1 et:
