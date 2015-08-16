pkgname=locale-info
pkgver=2.20
pkgrel=2
pkgdesc="Locale informations"
arch=('any')
url="http://www.gnu.org/software/libc"
license=('GPL' 'LGPL')
groups=('base')
depends=("glibc=${pkgver}")

source=(http://ftp.gnu.org/gnu/libc/glibc-${pkgver}.tar.xz{,.sig}
        localeinfo.sh)

sha256sums=('f84b6d42aecc288d593c397b0a3d02260a33ee686bce0c634eb9b32798f36ba5'
            'SKIP'
            '3c96d41a85f3b83debe4133cc922b08904960e15bff38ad9600ef4093d0c4646')


build() {
  cd ${srcdir}

  echo "building LOCALESINFO file..."
  chmod +x localeinfo.sh
  ./localeinfo.sh "glibc-${pkgver}/localedata/locales" LOCALESINFO
}


package() {
  cd ${srcdir}/glibc-${pkgver}

  install -dm755 ${pkgdir}/usr/share/i18n
  install -m644 localedata/SUPPORTED ${pkgdir}/usr/share/i18n/
  install -m644 ${srcdir}/LOCALESINFO ${pkgdir}/usr/share/i18n/
}

