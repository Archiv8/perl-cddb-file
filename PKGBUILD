#!/bin/bash

# Based on the original packaging by John D Jones III <j[nospace]n[nospace]b[nospace]e[nospace]k[nospace]1972 -_AT_- the domain name google offers a mail service at ending in dot com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/perl-cddb-file/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/perl-cddb-file/discussions>

_relname="CDDB-File"

pkgname="perl-cddb-file"
pkgver="1.05"
pkgrel="2"
pkgdesc="Parse a CDDB/freedb data file"
arch=(
  "any"
)
license=(
  "PerlArtistic"
  "GPL"
)
options=(
  "!emptydirs"
)
depends=(
  "perl"
)
# makedepends=()
_tarname="${_relname}-${pkgver}"
url="http://search.cpan.org/dist/CDDB-File"
source=("http://search.cpan.org/CPAN/authors/id/T/TM/TMTM/${_tarname}.tar.gz")
md5sums=(
  "c619e60e86a2bb227d434066c742b189"
)
sha512sums=(
  "569294e1b8e26b905915cc4c97dd1fd55d223a662deaba22258a452a5a0fb79e07ec8b0175715a34ad6d6ec3ecce794e04c7e17dd4ee8db22535ef75ef6d09fa"
)

build() {

  (
    export PERL_MM_USE_DEFAULT=1 PERL5LIB="" \
      PERL_AUTOINSTALL=--skipdeps \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR="${pkgdir}"" \
      PERL_MB_OPT="--installdirs vendor --destdir "${pkgdir}"" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/${_tarname}"

    /usr/bin/perl Makefile.PL

    make
  )
}

check() {

  cd "${srcdir}/${_tarname}"

  (
    export PERL_MM_USE_DEFAULT=1 PERL5LIB=""

    make test
  )
}

package() {

  cd "${srcdir}/${_tarname}"

  make install

  find "${pkgdir}" -name .packlist -o -name perllocal.pod -delete
}
