# Maintainer: Charles Bos <charlesbos1 AT gmail>
# Contributor: Xiao-Long Chen <chenxiaolong@cxl.epac.to>

pkgname=dee-ubuntu
_actual_ver=1.2.7
_source_date=20130924
_extra_ver=+13.10.20130924.1
pkgver=${_actual_ver}.${_source_date}
pkgrel=2
pkgdesc="Model to synchronize multiple instances over DBus"
arch=('i686' 'x86_64')
url="https://launchpad.net/dee"
license=('LGPL')
groups=('unity')
depends=('dbus-glib' 'glib2' 'icu' 'python' 'python-gobject' 'python2' 'python2-gobject')
makedepends=('gnome-common' 'gobject-introspection' 'gtk-doc' 'vala')
provides=("dee=${pkgver}")
conflicts=('dee')
source=("https://launchpad.net/ubuntu/+archive/primary/+files/dee_${_actual_ver}${_extra_ver}.orig.tar.gz")
sha512sums=('f59f0db206e4768999ab0977bbc98f60042946ed07380a7c3b4803f5dd90d63904999e6fe1042d642cadc44e0c58299ee4f4135fa02038fe38916a5618ec7e19')

build() {
  cd "${srcdir}/dee-${_actual_ver}${_extra_ver}"

  autoreconf -vfi

  mkdir build-python3 && cd build-python3
  PYTHON=python3 ../configure --prefix=/usr --enable-gtk-doc
  make
  cd ..

  mkdir build-python2 && cd build-python2
  PYTHON=python2 ../configure --prefix=/usr
}

package() {
  cd "${srcdir}/dee-${_actual_ver}${_extra_ver}"

  cd build-python3/
  make DESTDIR="${pkgdir}/" install
  cd ..

  cd build-python2/bindings/python/
  make DESTDIR="${pkgdir}/" install
}
