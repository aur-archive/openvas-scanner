pkgname=openvas-scanner
pkgver=3.4.0
pkgrel=3
pkgdesc="The OpenVAS scanning Daemon"
arch=('i686' 'x86_64')
url="http://www.openvas.org/"
license=('GPL')
depends=('glib2' 'openvas-libraries')
options=('!makeflags !buildflags')
# The file downloaded is determined by the `/1307/` part. Changing `pkgver`
#  does not change the file downloaded so we hard code the version number to
#  avoid confusion.
source=('http://wald.intevation.org/frs/download.php/1307/openvas-scanner-3.4.0.tar.gz'
        'openvas-scanner.service')
md5sums=('66c8d5baf4f5a070afcff04b779e8db7'
         '22c8b1e5522fb96c64360a7803f34db4')

build() {
  cd "$srcdir/openvas-scanner-$pkgver"

  cmake -DSBINDIR=/usr/bin -DCMAKE_INSTALL_PREFIX=/usr -DSYSCONFDIR=/etc -DLOCALSTATEDIR=/var .
  make
}

package() {
  cd "$srcdir/openvas-scanner-$pkgver"

  make DESTDIR="$pkgdir/" install
  install -Dm644 "$srcdir/openvas-scanner.service" "$pkgdir/usr/lib/systemd/system/openvas-scanner.service"
}
