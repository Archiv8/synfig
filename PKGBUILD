#!/bin/bash

# Based on original packaging by Popolon <popolon@popolon.org>, Piernov <piernov@piernov.org>, Sergej Pupykin <pupykin.s+arch@gmail.com> and Franco Iacomella <yaco@gnu.org>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/synfig/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/synfig/discussions>

#_langname=""
_relname="synfig"
_partname="core"
#_cvsname=""

# pkgbase=
pkgname="${_relname}-${_partname}"
pkgver=1.5.1
pkgrel=1
# epoch=
pkgdesc="Professional, Open Source 2D Animation Software. Core package providing the CLI renderer"
arch=(
  "x86_64"
  "armv7h"
  "armv8"
  "riscv32"
  "riscv64")
url="https://www.synfig.org/"
license=("GPL2")
# groups=()
depends=(
  "boost-libs"
  "cairo"
  "ffmpeg"
  "fftw"
  "fontconfig"
  "freetype2"
  "glibmm"
  "imagemagick"
  "libdv"
  "libmng"
  "libpng"
  "libsigc++2.0"
  "libtiff"
  "libxml++2.6"
  "mlt"
  "ocl-icd"
  "openexr"
  "pango"
  "etl=${pkgver}"
  "zlib"
)
optdepends=(
  "openexr"
  "libsigc++"
)
makedepends=(
  "boost"
  "git"
  "intltool"
  "opencl-headers"
)
# checkdepends=()
provides=(
  "synfig"
)
conflicts=(
  "synfig"
)
replaces=(
  "synfig"
)
# backup=()
# options=()
# install=
# changelog=
source=(
  "${_relname}-${pkgver}.tar.gz::https://github.com/${_relname}/${_relname}/archive/v${pkgver}.tar.gz"
)
# noextract=()
# validpgpkeys=()
sha512sums=(
  "0c1dd53a445f037bcdb742d7c17d1d3a2039e80d3e49f5cd67119fb9792d96b47154874d5be42d36443b0d09c61b7864dfe33ebd5f3998783c54eb3cc936d11b"
)

# prepare() {

# Change to the Synfig Core directory
#cd "${srcdir}/${_relname}-${pkgver}/${pkgname}"
# }

build() {

  cd "${srcdir}/${_relname}-${pkgver}/${pkgname}"

  export PKG_CONFIG_PATH="/usr/lib/imagemagick6/pkgconfig"

  # Bootstrap as not installing using scripts at project root, i.e, ./1-setup-linux-native.sh, 2-build-production.sh
  ./bootstrap.sh

  intltoolize --force --copy

  # Run configure script
  ./configure \
    --sysconfdir=/etc/synfig \
    --prefix=/usr \
    --enable-option-checking \
    --disable-silent-rules \
    --disable-static \
    --enable-dependency-tracking \
    --with-imagemagick \
    --with-magickpp \
    --with-ffmpeg \
    --with-libdv \
    --with-libavcodec \
    --with-freetype \
    --with-fontconfig \
    --with-openexr \
    --with-jpeg \
    --with-opencl \
    --with-boost

  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool

  # Run make
  make 2>&1 | tee make.log
}

# check() {}

package() {

  # Change to the Synfig Core directory
  cd "${srcdir}/${_relname}-${pkgver}/${pkgname}"

  # Install Synfig Core
  make DESTDIR="${pkgdir}" install 2>&1 | tee install.log
}
