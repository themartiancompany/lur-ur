# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
_proj="hip"
pkgname=lur
pkgver="0.0.0.0.0.0.0.0.0.0.0.0.0.1.1.1.1"
_commit="111a92d798e32a28e20a6c58e58f926b0b4098cd"
pkgrel=1
_pkgdesc=(
  "Local user repository."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
group=(
 "${_proj}"
)
license=(
  AGPL3
)
depends=(
  "aspe"
  "libcrash-bash"
  "pacman"
)
_os="$( \
  uname \
    -o)"
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=()
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _tar="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum='b245547bdcdbfeb09f400305a4b515b6d49635be90f560a39302761fc2688571'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="c19542830a08fd512f8fa13049a854302d2bbaa040a8dbbf91b2b16d130ae913"
  fi && \
    source+=(
      "${_tar}"
    ) && \
    sha256sums+=(
      "${_sum}"
    )

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
