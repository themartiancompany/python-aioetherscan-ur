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
pkgver=0.9.5.1
_commit="9efbb8f550dedb92424cec7d213e3c556d33cf96"
pkgrel=1
_pkgdesc=(
  'Etherscan API async Python wrapper.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
# _ns="ape364"
_ns="themartiancompany"
_http="https://github.com"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=3.9"
  "${_py}-aiohttp>=3.4"
  "${_py}-asyncio-throttle>=1.0.1"
  "${_py}-aiohttp-retry>=2.8.3"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-poetry"
  "${_py}-poetry-core"
  "${_py}-wheel"
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
source=(
  "${_pkg}-${_commit}::${url}/archive/${_commit}.zip"
  # Release tarball - never released one
  # "${url}/archive/v${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
sha256sum=(
  'a2010c4430264e359bb3c47315f38dfa94efda90c5cd6a6eac2d7010b78fe61e'
)
b2sums=(
  'ef04d8bebe7428fb8df36e9173268cc162a5b9311f53134369e0d80b7d21f9889fb2ef5844a9075065a46d60dcad9d98a32de8fc013c015de6af5c5f92196526'
)

build() {
  cd \
    "${_pkg}-${_commit}"
  poetry \
    build
  # python \
  #   -m \
  #     build \
  #   --wheel \
  #   --no-isolation
}

package() {
  cd \
    "${_pkg}-${_commit}"
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
