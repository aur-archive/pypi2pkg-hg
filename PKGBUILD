# Maintainer: mitsuse <mitsuset - gmail>
pkgname=pypi2pkg-hg
pkgver=2
pkgrel=2
pkgdesc="a PKGBUILD generator for PyPI."
arch=('any')
url="https://bitbucket.org/mitsuse/pypi2pkg"
license=('GPL2')
depends=('python' 'python-jinja')
optdepends=()
makedepends=('mercurial')
conflicts=('pypi2pkg')
provides=('pypi2pkg')
source=()
md5sums=()

_hgroot="https://bitbucket.org/mitsuse"
_hgrepo="pypi2pkg"

build() {
    cd $srcdir
    msg "Connecting to Mercurial server...."

    if [ -d $_hgrepo ] ; then
        cd $_hgrepo
        hg pull -u || return 1
        msg "The local files are updated."
    else
        hg clone $_hgroot/$hgrepo || return 1
    fi

    msg "Mercurial checkout done or server timeout"
    msg "Starting make..."

    cd $srcdir/$_hgrepo
    python setup.py install --root=$pkgdir --prefix=/usr
}

