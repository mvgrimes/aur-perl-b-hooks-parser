# Maintainer: Mark Grimes <mgrimes at peculier.com>

pkgname=perl-b-hooks-parser
pkgver=0.16
pkgrel=1
pkgdesc="Interface to perl's parser variables"
_dist=B-Hooks-Parser
arch=('any')
url="https://metacpan.org/module/$_dist"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.10' 'perl-b-hooks-op-check' 'perl-b-hooks-endofscope' 'perl-test-exception')
options=('!emptydirs' purge)
source=(https://cpan.metacpan.org/authors/id/E/ET/ETHER/$_dist-$pkgver.tar.gz)
md5sums=('5db64fd81d0c294d86af241529131680')

# Setup environment to ensure installation in system perl and vender directory
clean_env() {
  unset PERL5LIB PERL_MM_OPT PERL_MB_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1 MODULEBUILDRC=/dev/null PERL_AUTOINSTALL=--skipdeps
}

build() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  /usr/bin/perl Makefile.PL
  make
)

check() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  make test
)

package() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  make install INSTALLDIRS=vendor DESTDIR="$pkgdir"
)

